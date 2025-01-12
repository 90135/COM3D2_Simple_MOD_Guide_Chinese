# 第 4 课，用形态键或 .anm 让物品动起来


## 什么是 ShapeKey 形态键

ShapeKey（形态键），是 3D 动画领域的一种通用技术。
在 Blender 中称为 ShapeKey

在其他 3D 软件中，这种技术可能会被称为不同的名称，比如：
 - Maya：称为 Blend Shape。
 - 3ds Max：称为 Morph Target。
 - Cinema 4D：也称为 Pose Morph。
 - Houdini：通常叫 Blend Shapes，但实现方法更加程序化。
 - Unity/Unreal Engine：多称为 Morph Target 或 Blend Shape。

简单来说，它允许你对你的网格做一些改变，然后保存在 ShapeKey 中。

比如放大或缩小某个物品，更改表情，等等

假设你有一个角色模型，你可以创建一个 “微笑” 的 Shapekey 和。当你调整这些 Shapekey 的值时，角色的表情就会从默认状态逐渐变为微笑。这样无需重新建模，你就能实现复杂的形变效果。

通俗点说，Shapekey 就像是 “模型变形的滑杆”，通过调整滑杆的值，你可以控制模型在不同形状之间的过渡，非常适合用来制作表情动画或一些细节的动态变化。

它只保存最终状态，中间的值都是通过计算得到的。

#### 为什么

因为在 COM3D2 中操作骨骼比较麻烦，基本只在拍照的时候有用。

而形态键，被很多插件支持，我们可以随时随地进行调整。

官方的腿粗细、欧派大小滑块，其实都是形态建。

## 做一个最简单的动画

拿出我们第三课做的翅膀，给翅膀做一个动画吧。

详细的怎么做形态键可以去看 blender 教程

首先在物体模式点击添加形态键，Basis 是基本形态，不可删除，其他形态键的变形都是基于 Basis 的。

这个模型已经有形态键了，所以我们只需要添加一个我们自己的，否则就需要添加 Basis 再添加自己的。

![图片](https://github.com/user-attachments/assets/d046a2a2-e2db-4da4-86fb-e72298dbde0d)

添加后，切换到编辑模式，点击这个按钮，然后把值调整到 1，这时我们就可以调整模型了，形变，位移，都是可以的。

![图片](https://github.com/user-attachments/assets/7d4d56e0-6394-4079-b350-6bb2d1c02a45)


我这里旋转 + 位移了一下

![图片](https://github.com/user-attachments/assets/96447375-a924-441a-9369-a89273f2626a)

做完后拉动数值条就能看到效果了

![222](https://github.com/user-attachments/assets/0c797697-f8a6-4176-bbbe-1f362e9066e0)

导出后到游戏内，使用操作形态键的插件就能看到效果了。

比如 [ShapekeyMaster](https://github.com/krypto5863/COM3D2.ShapekeyMaster) 或 [ShapeAnimator](https://github.com/InoryS/COM3D2.ShapeAnimator.Plugin)

我这里用 ShapekeyMaster(要在简单模式添加键，然后在取消简单模式，展开，然后才能编动画)，效果如图

![333](https://github.com/user-attachments/assets/9bdecb4f-3c33-4c9d-9989-69c11311529e)

就是这么简单，恭喜你已经学会了创建形态键和在游戏内使用。


## 形态键的秘密

先跟着我做等下再告诉你为什么。

添加一个 body001（前面的课有说在哪哦）

然后在肚子这里，紧贴着放一个东西

比如我把第三课的翅膀删掉其他的，只剩下一个

![图片](https://github.com/user-attachments/assets/07232d99-aebd-4478-9304-f63d41299f9f)

然后添加一个形态键叫做 hara，在值为 1 时把它离远一些

![图片](https://github.com/user-attachments/assets/db5f7ee2-106d-406b-82a3-0208b78bffa5)

![444](https://github.com/user-attachments/assets/63196782-58ba-41cf-ab2b-f6518766ecdb)

进入游戏内编辑模式

调整身体的腹部大小，它居然会跟着动

![555](https://github.com/user-attachments/assets/c2c8451c-dd6d-4fa7-a4b5-811ecc3451ef)

这是为什么呢？


回到 blender 添加一个 body001（前面的课有说在哪哦），你会发现，这个身体上本来就有一些形态键，而 body001 就是官方标准身体。

![图片](https://github.com/user-attachments/assets/5a9d5333-d96c-4962-8df4-d1096603b9fd)

动一动这些形态键，你会发现有的是控制欧派大小的，有的是手臂粗细，腿粗细。

![图片](https://github.com/user-attachments/assets/af1b1707-c2ea-43e2-833c-816e492593a6)

<br>

你可能猜到了 **游戏内形态键是不分部位的** 当游戏自己去尝试调整形态键时，所有同名形态键都会跟着一起调整。

所以我们需要在衣服上做出同名形态键，来让衣服能够跟着身体一起变化（非官方身体有着更多的形态键）。

除此意外的调节就是骨骼了，而不是形态键。

<br>

当然你可以选择手动去做，但是这样就太麻烦了不是吗？

幸好我们的 blender 插件提供了形态键转移功能。

### 转移形态建

也可参阅：[https://github.com/Pain-Brioche/COM3D2-How-to/blob/master/Transfer_shapekeys_V2.md](https://github.com/Pain-Brioche/COM3D2-How-to/blob/master/Transfer_shapekeys_V2.md)

所谓转移形态键，就是把一个模型的形态键转移到另一个模型。

比如你做了一件透明紧身衣，没办法通过第一课的隐藏身体的方法来逃课。

所以我们需要在衣服上做出同名形态键，来让衣服能够跟着身体一起变化。

<br>

当然你可以选择手动去做，但是这样就太麻烦了不是吗？

幸好我们的 blender 插件提供了形态键转移功能。

首先我们把转移来源不需要的形态键删掉，我这里就不删了（否则形态键较多的身体会要很久）

我这里就用刚刚的模型演示了，先把刚刚添加到 hara 形态键删掉

<br>

然后在物体模式下，点击转移来源网格，然后按住 shift 点击转移目标

正确的话，颜色就会变成这样：

![图片](https://github.com/user-attachments/assets/19b48cf7-f558-46f9-b7d5-f115c7e73412)

然后点这里，一般选第二个

![图片](https://github.com/user-attachments/assets/787c4d68-7cbd-49a9-b885-fb4b62ba348a)

确定即可

![图片](https://github.com/user-attachments/assets/2d1cdb55-8fe0-45b7-8430-925124377387)

然后就会多出来几个形态键，插件认为没有影响的形态键是不会被转移的。

![图片](https://github.com/user-attachments/assets/6d2b68bd-3fd0-4b3e-92a2-1be9980ba231)

动一动，看看有什么效果吧。

和我们手动做的效果有点不太一样，所以想要精细的还得手搓。

![666](https://github.com/user-attachments/assets/4a23fba1-11ba-4218-8463-904effdff19d)

![777](https://github.com/user-attachments/assets/11d091f2-fe82-4c16-9d73-ea86cafd168d)

学会了形态键的秘密后，我们就可以移植衣服了。

## 使用 .anm

刚刚做的翅膀有一个明显的缺陷，用形态键做的动画，不能做到振翅，只能往一个方向移动（也不是不行，但是太过复杂）

所以我们需要使用 .anm

要做动画，我们最好给我们的翅膀添加上骨骼，方便操作

你需要看一些 blender 动画教程，blender 操作我不会教的太详细。

<br>

选中骨架，编辑模式点击添加骨骼，然后移动到合适的位置

![图片](https://github.com/user-attachments/assets/f541b660-cda6-45d9-bb13-6ebc4ef70e83)

添加以后如果选中布料，那么这里选中就能移动了

![图片](https://github.com/user-attachments/assets/16a6f9ff-93bc-467b-956b-44e8874b39f3)

移动到合适位置，然后给另外一边也加上（镜像什么的），然后改个名

![图片](https://github.com/user-attachments/assets/795d7636-ea90-4b8a-9470-7e56575f11e2)

别忘了之前说的顶点组和骨骼的关系

新建同名顶点组并设置权重为 1

注意有一个坑，如果你做什么复杂模型有很多骨头，那么一个顶点最多分配给 4 个顶点组
（.model 文件会将一个顶点分配给恰好四个顶点组。它不能存储超过四个。如果少于四个，它将只将其余顶点分配给 Bip01 权重为 0 的顶点组。（例如，如果顶点仅分配给一个顶点组，它将把其他三个顶点存储为Bip01: 0.0。）这意味着您只能将一个顶点分配给 4 个顶点组。)

![图片](https://github.com/user-attachments/assets/eefec924-7c84-4b43-8c08-6a2e82ac8396)

先导出

#### 添加骨头后为什么导出后骨头就没了？（如何添加骨头）

由于我们加了骨头，所以导出时数据源要选骨架

否则导出后，再导入，你会发现你的骨头被删了

![图片](https://github.com/user-attachments/assets/90b96654-1350-4ed9-bbc5-fab2348a8afc)

<br>

这里推荐重启 blender，重新导入刚刚导出的模型，以此来检查是否正确

物体模式选中骨架，然后这里就会变成姿态模式，选择姿态模式。

![图片](https://github.com/user-attachments/assets/007f2b58-7fa6-4b47-a316-21c3a3f6f5c9)

在姿态模式移动骨骼，可以看到它能够控制我们的翅膀，就说明顶点组做对了

![888](https://github.com/user-attachments/assets/946abd49-560b-4626-afaf-34a202a4b203)

然后我们就可以切换到 animation 模式了（顶部中间）

我们这里用默认的动画摄影表模式

我这里先把翅膀打直，然后按右键选择插入关键帧

注意：虽然你可以单独调整，但是插入关键帧时最好两个骨头都选中再插入，因为动画摄影表允许你单独编辑骨头。

![图片](https://github.com/user-attachments/assets/27a4b46c-dee7-427e-ab1b-0082ae503c3c)

![图片](https://github.com/user-attachments/assets/86f4f180-62b4-4a80-adf5-b6bf107d206a)

![图片](https://github.com/user-attachments/assets/52894a9b-791f-43b8-b554-086b9d48eb0b)


然后移动下面的帧数到你喜欢的位置，移动翅膀，再插入一个关键帧

![图片](https://github.com/user-attachments/assets/84844931-8e01-4d8d-aff2-53eaf47d0f0b)

然后选中起始点，按 ctrl + c， ctrl + v 复制一下

再按 G 拖到合适位置

然后再设置结束点为 60 帧（因为我把关键帧拖到了 60 帧）

![图片](https://github.com/user-attachments/assets/14e10740-7023-4667-9e35-28829c7b4334)

最后点击播放，我们就得到了一个动画

![888](https://github.com/user-attachments/assets/037da182-a2aa-45b7-8a59-cf199c3b2259)

然后转换为 CM3D2 插值

![图片](https://github.com/user-attachments/assets/4d1c16c5-c44b-4cc9-a02a-e4904e4b0e0f)

然后导出

![图片](https://github.com/user-attachments/assets/261ecd9e-9eda-4cb6-b000-45c03da1d598)

如果你没有为刚刚加的骨头设置父级，那么这里要取消掉

当然，你最好设置父级，不然会乱动

然后，选只导出关键帧就够了，第一个选项坏了

![图片](https://github.com/user-attachments/assets/d5ca1a86-6425-4618-bb09-b80a253915a4)


![999](https://github.com/user-attachments/assets/5825823b-a72a-436a-9f80-15d3f3bd9ab1)


## 作业


# 第 5 课，做一双 HighHell 插件高跟鞋

## HighHell 插件是什么

COM3D2.HighHeel.Plugin InoryS 版插件，正如其名字，就是用来做高跟鞋的插件，相比于之前的 RV 高跟鞋，HH 插件高跟鞋不限制体型，不限制袜子，使用非常灵活。

我也贡献了而一部分代码，要是有 BUG 什么的可以找我。

他的仓库里都有说原理是什么，请先大致看一遍，有中文和英文版本。（注 foobar 是一个占位符，可以替换为你想要的词，包括单独的 foo 和 bar）

[https://github.com/InoryS/COM3D2.HighHeel](https://github.com/InoryS/COM3D2.HighHeel)

简单来说就是读取物体名，（并不是文件名，也不是 menu 名）物体名里面需要包含 `hhmod_foo`，不知道什么是物体名就往下看（黄色倒三角是物体/对象，绿色倒三角是网格）。
那么插件就去读取配置文件名为 `hhmod_foo.json` 的配置文件，配置文件里面写了脚的角度、脚趾的角度什么的，从而动态调整脚和脚趾的角度。

比如自带的 `hhmod_27d.json` 配置文件（实际的文件并不能有注释）：
```
{
  "BodyOffset": 0.04,    //默认女仆 BodyOffset，如果您没有为场景单独设置 BodyOffset，则应用此值。//如果你在中设置 EnableGlobalPreSceneOffsetSettings 为 false ，则使用此值，否则此值不会被使用
  "ManBodyOffset": 0.0,  //默认男人 BodyOffset，如果您没有为场景单独设置 BodyOffset，则应用此值。//如果你在中设置 EnableGlobalPreSceneOffsetSettings 为 false ，则使用此值，否则此值不会被使用
  "PerSceneBodyOffsets": {  //如果你在中设置 EnableGlobalPreSceneOffsetSettings 为 false ，则使用此值，否则此值不会被使用
    "SceneDaily":0.02,   //为每个场景单独设置的女仆 BodyOffset，这表示将场景名为 SceneDaily 的女仆 BodyOffset 设置为 0.02
    "SceneTrophy": 0.14,  //为每个场景单独设置的女仆 BodyOffset，这表示将场景名为 SceneTrophy 的女仆 BodyOffset 设置为 0.14
    "SceneYotogi": 0.04,
    "SceneFreeModeSelect": 0.14,
    "SceneYotogiOld": 0.05,
    "SceneDance_CKTCK_Release": 0.06,
    "SceneDance_CPM_K_2_Release": 0.06,
    "SceneDance_1OY_K_Release": 0.06
  },
  "PerSceneManBodyOffsets": {//如果你在中设置 EnableGlobalPreSceneOffsetSettings 为 false ，则使用此值，否则此值不会被使用
    "SceneDaily":0.02,  //为每个场景单独设置的男人 BodyOffset，这表示将场景名为 SceneDaily 的男人 BodyOffset 设置为 0.02
    "SceneTrophy": 0.06,  //为每个场景单独设置的男人 BodyOffset，这表示将场景名为 SceneTrophy 的男人 BodyOffset 设置为 0.06
    "SceneYotogi": 0.0,
    "SceneFreeModeSelect": 0.05,
    "SceneYotogiOld": 0.05
  },
  "FootLAngle": 27.0,   //左脚的 Z 轴旋转角度，因为这是 27d 配置文件，所以设置为 27
  "FootLMax": 88.0,     //左脚的 Z 轴最大旋转角度
  "ToeL0AngleX": 7.0,   //左脚的小脚趾的 X 轴角度
  "ToeL0AngleY": -17.0, //左脚的小脚趾的 Y 轴角度
  "ToeL0AngleZ": -17.0, //左脚的小脚趾的 Z 轴角度
  "ToeL01AngleX": 5.0,  //左脚的小脚趾前端的 X 轴角度
  "ToeL01AngleY": 0.0,  //左脚的小脚趾前端的 Y 轴角度
  "ToeL01AngleZ": 0.0,  //左脚的小脚趾前端的 Z 轴角度
  "ToeL1AngleX": 0.0,    //左脚的中间三脚趾的 X 轴角度（这是因为 KISS 只给它们分配了一根骨头）
  "ToeL1AngleY": 0.0,    //左脚的中间三脚趾的 Y 轴角度
  "ToeL1AngleZ": -27.0,  //左脚的中间三脚趾的 Z 轴角度
  "ToeL11AngleX": 0.0,   //左脚的中间三脚趾前端的 X 轴角度（这是因为 KISS 只给它们分配了一根骨头）
  "ToeL11AngleY": 0.0,   //左脚的中间三脚趾前端的 Y 轴角度
  "ToeL11AngleZ": 0.0,   //左脚的中间三脚趾前端的 Z 轴角度
  "ToeL2AngleX": -2.0,   //左脚的大脚趾的 X 轴角度
  "ToeL2AngleY": 0.0,    //左脚的大脚趾的 Y 轴角度
  "ToeL2AngleZ": -17.0,  //左脚的大脚趾的 Z 轴角度
  "ToeL21AngleX": 0.0,    //左脚的大脚趾前端的 X 轴角度
  "ToeL21AngleY": 0.0,    //左脚的大脚趾前端的 Y 轴角度
  "ToeL21AngleZ": -14.0,  //左脚的大脚趾前端的 Z 轴角度
  "FootRAngle": 27.0,    //右脚的 Z 轴旋转角度，因为这是 27d 配置文件，所以设置为 27
  "FootRMax": 88.0,      //右脚的 Z 轴最大旋转角度
  "ToeR0AngleX": -7.0,   //左脚的小脚趾的 X 轴角度
  "ToeR0AngleY": 17.0,   //左脚的小脚趾的 Y 轴角度
  "ToeR0AngleZ": -17.0,  //左脚的小脚趾的 Z 轴角度
  "ToeR01AngleX": 0.0,   //左脚的小脚趾前端的 X 轴角度
  "ToeR01AngleY": 0.0,   //左脚的小脚趾前端的 Y 轴角度
  "ToeR01AngleZ": 0.0,   //左脚的小脚趾前端的 Z 轴角度
  "ToeR1AngleX": 0.0,    //左脚的中间三脚趾的 X 轴角度（这是因为 KISS 只给它们分配了一根骨头）
  "ToeR1AngleY": 0.0,    //左脚的中间三脚趾的 Y 轴角度
  "ToeR1AngleZ": -27.0,  //左脚的中间三脚趾的 Z 轴角度
  "ToeR11AngleX": 0.0,   //左脚的中间三脚趾前端的 X 轴角度（这是因为 KISS 只给它们分配了一根骨头）
  "ToeR11AngleY": 0.0,   //左脚的中间三脚趾前端的 Y 轴角度
  "ToeR11AngleZ": 0.0,   //左脚的中间三脚趾前端的 Z 轴角度
  "ToeR2AngleX": 2.0,    //左脚的大脚趾的 X 轴角度
  "ToeR2AngleY": 0.0,    //左脚的大脚趾的 Y 轴角度
  "ToeR2AngleZ": -17.0,  //左脚的大脚趾的 Z 轴角度
  "ToeR21AngleX": 0.0,   //左脚的大脚趾前端的 X 轴角度
  "ToeR21AngleY": 0.0,   //左脚的大脚趾前端的 Y 轴角度
  "ToeR21AngleZ": -14.0  //左脚的大脚趾前端的 Z 轴角度
}
```



## 移植一个 MMD 鞋子

这次的模型来自

[https://www.deviantart.com/lastwolfer/art/HHsandalI-Ver340-865859283](https://www.deviantart.com/lastwolfer/art/HHsandalI-Ver340-865859283)

![图片](https://github.com/user-attachments/assets/5e26ac86-eda5-4ec2-b476-53d4e0a8acc3)


如果打不开需要使用非机房 IP 访问。

没有许可证

<br>

部分内容在前面的课教过了省略

一样的导入后删除骨骼，这个模型还带了一段腿，把腿脚也删了

![图片](https://github.com/user-attachments/assets/769b737d-381e-4691-86d8-0eaff27414c6)

直接编辑模式选中腿的顶点，按 ctrl + + 加选就行了。

![图片](https://github.com/user-attachments/assets/ceafa7f2-673a-4aa8-a905-b5c986633037)

删掉一只鞋，等下我们用镜像

这个模型还有指甲，记得也删了

<br>

### 粗略对齐


添加一个 T-pose 的 body001 

![图片](https://github.com/user-attachments/assets/5df035e9-95d3-4d08-9b15-6a1881cfa763)


切换到正交视图，然后跳转到合适大小和角度

![图片](https://github.com/user-attachments/assets/f88f79db-207f-4510-94a5-afb7d1758606)


![图片](https://github.com/user-attachments/assets/c396db55-bd8e-4128-bab9-d306f3ae0050)


![图片](https://github.com/user-attachments/assets/2e111aa3-5897-44bd-8a52-cf170651347c)


### 以任意姿势导出

先导出看一眼效果再回来仔细调整

原先的骑摩托姿势会给我们对齐造成很大麻烦，所以我们这里学习一下如何以任意姿势导出

物体模式选择 T-pose 的骨架，点导出 .anm，我这里叫 t.anm

![图片](https://github.com/user-attachments/assets/7a8a400a-a551-4919-b56d-b19c76c24119)

这个导出的 t.anm 以后可以复用

然后把 T-pose 的 body001 的骨架和网格都删掉

重新添加一个标准的 body001（摩托姿势）

选中 body001 的骨架，点导入 .anm，把刚刚的 t.anm 导入

![图片](https://github.com/user-attachments/assets/d77b28e8-7fbf-4e0b-a88b-3dc2c94db834)

就会发现它变成 T-pose 了

![图片](https://github.com/user-attachments/assets/084480b2-eda8-4bed-ba68-db907e4f280d)

切换到姿态模式，这里有个 Apply Prime Field，点他

![图片](https://github.com/user-attachments/assets/902b8fce-defb-4997-9242-c9ad93d4c941)

成功以后这里就可以切换姿势了

![图片](https://github.com/user-attachments/assets/89848a6d-222a-4f25-9f6f-0426000d2805)

![图片](https://github.com/user-attachments/assets/643968ec-2d8d-4da9-b2d4-cf7eec38f550)

![图片](https://github.com/user-attachments/assets/8c8f5db9-e9a1-403b-87eb-7713e55ad6fb)

但是你会发现，在右上角 拖动网格 + shift 设置父级以后，切换姿势鞋子还是没有跟着动（骨骼跟随原理在第三课）

（注意，不是右键或 Ctrl+p 设置父级为骨架形变，那样设置父级后会自动添加修改器的，很可惜很多绑骨教程都没有说明这一点）

![图片](https://github.com/user-attachments/assets/37babe3e-33f2-42ec-b5d9-f7e7ec062e70)

因为实际上，骨骼和网格是完全独立的两个物体，相互之间没有关系，移动一个物体为什么另一个物体会跟着动呢？

当然不会咯

那你问为什么身体会跟着动？那是因为，身体有一个修改器

游戏内为什么会跟着动？你可以理解为游戏自带一个修改器

![图片](https://github.com/user-attachments/assets/a71fbca7-e1e8-41e7-9038-ff010c7456a0)

网格和骨架之间是靠修改器才有的对应关系，包括我们导入 MMD 模型后，会有一个 MMD 骨架修改器。

所以我们自己添加一个修改器就行了（这里添加修改器只是编辑方便，不影响导出和游戏内效果，你可以理解为游戏内自带一个修改器）

![图片](https://github.com/user-attachments/assets/20833ebf-77a2-4c7d-a799-d316e2942c82)

物体选择骨架，你就会发现鞋子也过去了

![图片](https://github.com/user-attachments/assets/2c6c5f0a-3db9-49b2-a628-e049a635f327)

当然你会发现编辑模式鞋子又回去了，勾上这两个选项就好

![图片](https://github.com/user-attachments/assets/1abd3e8d-1be4-4c38-b54f-a6af076297b8)


![图片](https://github.com/user-attachments/assets/87bf2c1c-5f02-4b42-8e60-f1a3db602c63)

这样你就可以轻松在姿势之间切换了，找一个方便编辑的姿势就好，一般都是 T-pose

当然导出时数据源要选骨架

![图片](https://github.com/user-attachments/assets/ab770c8a-7c9c-4ff8-b7d8-1f0f8ba3986e)


### 导出

前面的课都有教，这里略

记得应用变换

转换下材质，我们先进游戏看看效果

编辑模式下，这里会有选择，你可以点选择看看这个材质影响哪些顶点。

然后把不需要的材质删掉。（小三角那里有个删除未使用槽）

![图片](https://github.com/user-attachments/assets/a9806541-c0b2-4153-bec4-6f6d44473b94)

一样的，为鞋子分配顶点组（前面的课有讲什么原理）

![图片](https://github.com/user-attachments/assets/a9b1df68-0997-41c8-8bd5-5ef029b05593)


![图片](https://github.com/user-attachments/assets/de6711cf-7a28-4140-833f-1b3a6883e1e8)


![图片](https://github.com/user-attachments/assets/3ecca2c6-02b3-47f1-9929-bc9033111f3a)

![图片](https://github.com/user-attachments/assets/0005f7c0-9c4d-4690-8ad3-614113eb9b41)


### 进游戏

进游戏大概就是这样的，脚和脚趾的旋转角度等下靠插件调整，我们只需要把鞋子对齐脚底就行了

鞋子上的线是贴图自带的。

![图片](https://github.com/user-attachments/assets/0d02afba-13bd-438d-9600-b064b372b2ba)


### 精修模型

很明显无论是 RV 的鞋，还是 MMD 的鞋，脚大小都是不一样的，我们需要自己调整模型

进入游戏，按 ctrl + F9 呼出插件设置，慢慢调整角度，直到合适（Foot L Angle 意思就是 脚 左 角度）

我这里调出来是 42 度，42d ~= 5.9 英寸（150 毫米）高跟鞋（22.5 * sin(45π/180) ~= 15.055439）（善待你的妹抖!） 22.5cm 是 COM3D2 默认体型的大概脚长度

![图片](https://github.com/user-attachments/assets/4bbc3eec-0459-42a2-906c-280f4aded0ea)


然后我们再回到 blender 去不断调整角度，当然不可能完全对齐的，因为脚形是不一样的。

![图片](https://github.com/user-attachments/assets/90ee3aa1-143b-4c19-8c5f-3da9cf67c172)

在尽可能对齐脚以后，剩下的部分我们通过雕刻模式或者衰减编辑来进行调整（当然你会其他的也行，强烈建议学习一下晶格和晶格修改器）

比如用雕刻模式的抓取，往外推，或者拉，把绑带外移

![图片](https://github.com/user-attachments/assets/8f50b3e8-6d78-42d8-a2a4-72beae99d9da)

差不多就是这样，要穿袜子还要再往外移。

![图片](https://github.com/user-attachments/assets/8c3b5585-7bfa-4308-bfeb-0d2aa44daecb)

剩下的就是靠个人 blender 水平了

大概就是这样

因为其实我并不喜欢这双鞋，所以只是随便调了一下做演示，所以歪歪扭扭的

![图片](https://github.com/user-attachments/assets/50443707-307a-4330-9174-e232d1678e9d)

为什么有黑块？ 别忘了之前教的哦，这是面朝向不对。（因为我随便编辑把里面的面拉出来了）

### 做另一只鞋

直接镜像就行了，有很多种办法，我这里用镜像修改器（其他办法可能面朝向也会镜像，记得检查）

![图片](https://github.com/user-attachments/assets/ec717acd-f024-48ea-9192-3347f281818e)

可以看到直接就在对应位置上了，点应用

![图片](https://github.com/user-attachments/assets/c59a4dfc-ec8d-4b26-b19a-bf28cb6b44cf)


导出到游戏内，会发现位置不对

![图片](https://github.com/user-attachments/assets/b215935a-aea9-4c9e-a76f-1f3a7f75398d)


回想一下之前教的物体跟随原理，我们需要调一下顶点组

把右边鞋子绑定到右脚骨上

![图片](https://github.com/user-attachments/assets/9e339a4b-65a2-41be-ab23-0928842ba064)

然后再把左脚骨对右边鞋子的权重删掉（因为镜像出来的，顶点组当然也镜像了）

选中右边鞋子的网格，点移除就行了

![图片](https://github.com/user-attachments/assets/a4b7c35c-1d9a-4ab0-a489-f740994399ab)

效果

![图片](https://github.com/user-attachments/assets/a57d515e-4c35-4ea0-8e6c-b08bbcfc68b6)


### 收尾

别忘了插件的原理，插件会读取物体名

hhmod_xxxx 以 _ 为分隔符，也可以添加别的内容，例如 90135_hhmod_42d_shose

![图片](https://github.com/user-attachments/assets/ca73da43-ea4b-470c-a51a-a0568283a3e5)

我这里插件就回去配置文件夹读取 hhmod_42d.json 这个配置。


在插件调整完后点导出

![图片](https://github.com/user-attachments/assets/cfac8d44-5971-4598-b225-64604f983641)

控制台会告诉你在哪里 `COM3D2\BepInEx\config\COM3D2.HighHeel\Configurations`

![图片](https://github.com/user-attachments/assets/3a2e75d5-125b-451a-a13d-fc6666e1ae81)

关掉编辑模式，点一下刷新，配置文件就应该自动读取了。

![图片](https://github.com/user-attachments/assets/be6ea904-886e-487f-bc50-044adf33ca7c)

如果你用的不是自带的配置文件，再分享时别忘了把配置文件也分享给他


### 另一种方法

ymk 大佬制作了 13d、20d、27d、34d 高度的 .anm 文件

可以在首页 ymk 移植教程中，或者本仓库[素材包](https://github.com/90135/COM3D2_Simple_MOD_Guide_Chinese/tree/main/%E7%B4%A0%E6%9D%90%E5%8C%85)内的 hh_anm.zip（已获授权）

导入后如图，这样就可以比平底对齐更直观的做鞋了

只是上文的 t.anm 换成了这个，本质没有什么不同，还是按任意姿势导出的方法导出即可。

![27d](https://github.com/user-attachments/assets/e5ea44b8-eb4b-4472-ace0-42a668fa8ef4)



## 作业

移植一双自己喜欢的高跟鞋





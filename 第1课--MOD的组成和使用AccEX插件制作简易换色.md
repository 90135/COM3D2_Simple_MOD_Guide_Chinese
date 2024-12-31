# 第 1 课，MOD 的组成和使用 AccEX 插件制作简易换色

## MOD 的组成

首先我们知道游戏内的物体都是 3D 模型。

3D 模型里面大概有这么几种东西

- Model （网格）
- Shader（着色器）
- Material（材质） 
- Texture（纹理）
- Texture Map（贴图）

简单来说

- 模型，决定物体的形状，点线面信息，实际的点线面称为网格。COM3D2 里面是 `.model` 文件（.model 内可以包含材质和着色器信息，因此可以省略 .mate 文件）
- 贴图，决定物体的颜色等，就是一张图片，COM3D2 里面是 `.tex` 文件（png 图片转的）
- 材质，决定贴图怎么渲染到物体上，COM3D2 里面是 `.mate` 文件
- 着色器，决定怎么渲染物体，COM3D2 里面有带不带轮廓线、是不是透明之类的着色器，在 `.mate` 里面指定。

一些 COM3D2 才有的东西

- `.menu` 文件，菜单，你在物品栏里面看到的东西都是一个个 menu，用来指定这物体用哪个模型，哪个材质等等，包括那个脱下装备的都是 menu。
- `.pmat` 用于指定渲染顺序，只有用透明着色器的时候才用得到
- `.phy` 物理信息文件，如果你想搞一些有物理效果的东西，需要使用这个
- `.col` 碰撞箱信息，如果你想搞一些有物理效果的东西，需要使用这个
- `.psk` 裙子专用物理信息文件
- `.anm` 动画文件，你可以给模型做一个动画，然后在 menu 内指定使用该 anm

一个最精简的 mod 只需要 `.menu`、`.tex`、`.model`

理解组成部分以后

我们通过案例来加深对 MOD 组成的理解

## 提示

在做 mod 的过程中，经常会有修改一点，在游戏里面查看更改效果的需求，然而你肯定不想重新启动游戏。

首先你需要在游戏启动前准备好就你的 .menu 和需要的文件

一旦游戏加载，它就会记住文件名，而不会记住内容。

所以你可以直接在游戏内修改，对应的 .menu 文件、.mate 文件、.model 文件（.tex 文件有时候可以，有时候不能，直接拿 AccEx换得了）

然后换到别的物品，再换回来你的，你就会发现它读取了最新的内容。

当然，.menu 文件不是所有内容都能重新加载的



(图标不能重新加载)

但是不能新增文件，因为 BUG 很多。

虽然新增的文件通过 MaidLoader 的刷新功能也能加载进来。

## 对官方物品进行修改

### 提取官方物品

以官方的 dress118_stkg_i_.menu 为例

#### 找到文件名

按 Shift + I 打开 PropMyItem InoryS 版

在袜子栏搜索 118，我有这么多是因为我有 MOD

![图片](https://github.com/user-attachments/assets/abc4759c-9b2f-4d25-9235-18bd5d07e79a)

装备上后在控制台可以看见这个物品的 menu 名称（只有 InoryS 版才会显示）

如果你不想换，在安装 SybarisArcEditor（在英文工具包里） 的情况下，在编辑模式一起按下 M O D 三个键，左上角就会有一个导出，此时装备一个物品，然后点导出，就能看到文件名。

#### 提取文件

由于是官方物品，我们需要使用 SybarisArcEditor（在英文工具包里）  从游戏文件内提取这个袜子的相关文件

如果你没安装，把 SybarisArcEditor.exe 放到 COM3D2.exe 旁边就行了

![图片](https://github.com/user-attachments/assets/68c9f72a-2dcc-4dc6-80ad-0bcdbd06deec)

打开后会很卡，耐心等一会

然后你会发现 dress118_stkg 什么都搜不到

那是因为这是从 CM3D2 联动过来的，这就是为什么有的东西你找不到

去 CM3D2 那边打开 SybarisArcEditor

可以看到官方文件种类和 dlc 名称进行了分类

![图片](https://github.com/user-attachments/assets/9cc53d34-156c-4126-8d79-4582741b7d85)

依次点开，你会发现有 .mate .menu .model 和几个 .tex

依次右键，点保存

得到以下几个文件，还记得之前说的组成吗？

![图片](https://github.com/user-attachments/assets/6ae375de-212f-4868-9ae8-7127e42d9939)

### 修改官方物品

很久以前， KISS 官方推出了 .mod 格式，现在已经淘汰了
随着 Modloader 和 MaidLoader 的出现，它允许我们直接以官方物品的格式来加载物品

.menu 其实就是个 txt 文件，只不过内部要遵照一定的格式

目录说的 English Modding Tools Pack 里面的 Core Modding Tools (English)
里面有一些看了名字就知道是做什么的用的东西

#### menu

用工具转成 txt 或用编辑器打开 .menu

这里用我自己做的 menu 编辑器打开，本来我都是用某 D 的工具，但是他禁止外国人使用。

为了大家有相对好用的工具，只好自己做了

![图片](https://github.com/user-attachments/assets/fc89861f-debb-47e4-bb63-54e443bf35e6)

可以看到 menu 的基本组成

menu 文件详细请参考
https://seesaawiki.jp/com3d2mod_wiki/d/menu

我们把东西都改个名，比如都改成 learn

注意文件不能以 mod 开头，不然你会发现它读不了，看了源码也没发现为什么

(MODフォルダにMODファイルが見つかりません。)

![图片](https://github.com/user-attachments/assets/b278da2a-8430-4f6b-a1d1-64f55c8b9528)

然后打开 menu 编辑，编辑指向对应文件

![图片](https://github.com/user-attachments/assets/b3895ac4-c11a-4f96-8a8a-c95e5553a4d0)

#### mate

那么你会问其他的 2 个 .tex 是在哪里指定的？

答案是，可以在 .model 或 .mate 里指定，

.meta 可有可无，如果你指定了 .mate，那么就会覆盖 .model 原版指定的内容

（所以可以通过添加多个 .meun 和 .mate 组合来制作换色 mod 而不需要修改 .model）

用 mate 编辑器或者转成 txt 打开 .mate 文件

![图片](https://github.com/user-attachments/assets/ca1510ea-bd92-4eb7-97df-4412c215dfe5)

改成对应贴图名字，但不带 .tex
那个路径没什么用，可以忽略，随便填个东西就行了(COM3D2 2.06 +)

![图片](https://github.com/user-attachments/assets/f849350f-f2fe-4de6-9974-64b36b1b743f)

mate文件详情请参考
https://seesaawiki.jp/com3d2mod_wiki/d/mate

#### tex

用 TexTool 打开 .tex，会转成 .png

用 TexTool 打开其他格式图片，会转成 .tex

打开 mod_learn.tex 用你最爱的图片编辑器编辑一下

作为示例，我们这里乱画一点东西

![图片](https://github.com/user-attachments/assets/06ac51a8-9b8b-4133-a90d-0c7f5b569a30)

然后再转回 .tex

同理 mod_learn_i_.tex 这个是我们在 menu 里面指定的图标，也是画点东西在上面

![图片](https://github.com/user-attachments/assets/5998590b-a56f-4965-8df2-310817490638)

#### 进游戏

把刚刚的文件都放到 MOD 文件夹里，然后启动游戏

![图片](https://github.com/user-attachments/assets/025de591-96bb-4fdd-b954-d97298d879dd)

铛铛
发现刚刚乱画的线条了吧

![图片](https://github.com/user-attachments/assets/842f4a42-5f16-4537-b622-89b980278cf1)

然后我们发现后面的贴图并没有被画

取决于光照方向，非光照面会使用 _ShadowTex 中的贴图，我们没有修改，所以不会有变化

![图片](https://github.com/user-attachments/assets/634f4663-6e93-4c04-93a2-fa69e28f7850)


恭喜你已经学会了 MOD 的基本组成

### 对别人的 MOD 进行修改

同理，只不过不需要提取了罢了

## 使用 AlwaysColorChangeEx

我们可以使用 AlwaysColorChangeEx 轻松完成刚刚的操作和编辑 mate

### 和 mate 文件的对应关系

![图片](https://github.com/user-attachments/assets/ebb230ac-49a0-49cc-b886-ff9b4fdee61d)

color 只会对 _MainTex 生效

![图片](https://github.com/user-attachments/assets/270ecffc-2901-4a5c-86b3-c1bdcb844dde)

![图片](https://github.com/user-attachments/assets/7f6202c8-4979-441b-8b0a-829f1d2b6bea)

点纹理更改按钮

![图片](https://github.com/user-attachments/assets/864b107f-8cc4-48ff-8347-477770026c97)

点这个就能更换贴图了
可以直接读 .png 格式的

![图片](https://github.com/user-attachments/assets/ea22d8b3-ecf0-48d6-9081-68b2a3015dee)

你可以自己调节各种参数尝试,，然后点击 menu 导出就能导出了
会导出到 MOD/ACC 文件夹

#### 素材包

本人提供的 MOD Thicc_Socks_109 中 提供了许多贴图，你可以自己更换尝试，非常有助于理解

- https://zodgame.xyz/forum.php?mod=viewthread&tid=470514&extra=page%3D1
- https://mega.nz/folder/U6Jy0a6a#Pv5G9G_J5zoYc46TVmz6iA

### 使用 AlwaysColorChangeEx 来修改 MOD

#### 修改着色器

如图就是着色器，你可以自己试试

比如我们这里选择透明着色器，但是发现腿没了

![图片](https://github.com/user-attachments/assets/09cad8a5-af87-491e-9ba3-9734b721ca32)

还记得 menu 文件里的   消去node設定開始  吗

![图片](https://github.com/user-attachments/assets/816ed6a9-5e23-434d-b44f-83b87594b0a8)

就是它把腿隐藏了
我们把它删了再看看

![图片](https://github.com/user-attachments/assets/d6bd7f5f-7ea8-4a34-b2a0-49fa1e584b42)

可以看到大腿就显示出来了，但是有点穿模

![图片](https://github.com/user-attachments/assets/682da734-3d70-4d99-9373-8849d2405862)

#### 渲染顺序

RQ 是 renderQueue

一般透明材质要设置为 3000+

可以看出明显区别

![图片](https://github.com/user-attachments/assets/4a77035e-a774-4ad5-9c72-ca01c4e216bb)

![图片](https://github.com/user-attachments/assets/eba40c63-f0fa-4f79-9292-b11da2fe47e0)

鞋子我也调成透明材质了
它的 RQ 是 3071
可以看到，当我们把袜子渲染顺序调到 3072 后，鞋子的显示发生了变化

![图片](https://github.com/user-attachments/assets/416ff4bb-8e09-453d-859c-341c34a76470)

## 作业

* 将 `dress118_stkg` 恢复原贴图。
* 将贴图颜色改为蓝色。
* 设置为透明材质并调整 `RQ` 顺序。
* 导出为完整的 MOD 文件。

大致效果

![图片](https://github.com/user-attachments/assets/f621329d-5c1f-45bd-a14f-704cc13023e3)


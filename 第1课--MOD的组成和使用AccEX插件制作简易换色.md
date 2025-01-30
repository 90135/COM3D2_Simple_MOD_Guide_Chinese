# 第 1 课，MOD 的组成和使用 AccEX 插件制作简易换色

## MOD 的组成

在游戏开发中，游戏内的物体本质上都是由 3D 模型组成。

一个完整的 3D 模型通常包含以下几种元素：

- **Mesh（网格）**：定义物体的形状，包括顶点、边和面等信息。
- **Shader（着色器）**：决定物体的渲染方式，如光影效果、透明度等。
- **Material（材质）**：定义贴图如何被渲染到网格上，包含与着色器的关联。
- **Texture（纹理）**：一种图片资源，用来描述物体表面的细节，如颜色、光滑度等。
- **Texture Map（贴图）**：进一步细分的纹理，用于不同用途，例如法线贴图、光照贴图等。

平时基本把 Texture 和 Texture Map 都叫做贴图。

简单来说：
1. **模型（Model）**：模型是一个可以包含多种信息的文件，其中可以包含物体的点线面信息（称为网格）定义物体形状，包含材质信息等。在 COM3D2 中是 `.model` 文件，且 `.model` 文件可以包含材质和着色器等信息，因此可以省略 `.mate` 文件。
2. **贴图（Texture）**：定义物体的表面细节，例如颜色和质感。COM3D2 中对应 `.tex` 文件（本质是 PNG 图片的转换）。
3. **材质（Material）**：描述贴图如何渲染到模型上。COM3D2 中使用 `.mate` 文件（`Material` 的缩写）。
4. **着色器（Shader）**：决定物体的渲染方式，例如是否有轮廓线、透明效果等。在 `.mate` 文件中指定。

### COM3D2 特有的文件类型
以下是一些特定于 COM3D2 的文件：
- **`.menu` 菜单文件**：游戏物品栏中看到的每个物品几乎都由 `.menu` 文件定义，用于指定这个物品使用什么模型、使用什么图标等等，包括男选择界面，以及脱下物品的选项都是一个个 `.menu`。
- **`.pmat` 文件**：用于定义渲染顺序，基本只在使用透明着色器时有用。
- **`.phy` 文件**：物理信息文件，提供物体的物理行为，例如摇动效果。
- **`.col` 文件**：碰撞箱信息文件，用于实现物体的物理交互。
- **`.psk` 文件**：专用于裙子物理模拟的信息文件。
- **`.anm` 文件**：动画文件，可以为模型创建动画效果，并在 `.menu` 文件中指定。

### 最简化的 MOD
制作一个最精简的 MOD，通常只需要以下文件：
- **`.menu`**
- **`.tex`**：
- **`.model`**：

甚至 .tex 都可以不需要

<br>

大概理解组成部分以后

我们通过案例来加深对 MOD 组成的理解

## 提示
在制作 MOD 的过程中，经常会遇到需要修改一点内容并立即在游戏中查看效果的需求。为了节省时间，你可以避免每次都重启游戏。

看不懂可以先跳过这个部分。

**文件准备**
1. 游戏加载时只会记住文件的名称，而不会记住其内容，也不会记住路径（如果你使用 MaidLoader 的话是这样的）
2. 同名文件只会加载最后被读取的那个
3. 游戏记住文件名以后并不会去读取文件内容。（当然进入加载模式时游戏会读取 .menu 内的图标和物品名字/描述都，否则你就看不到物品列表了）
4. 在你装备物品时，游戏才会去读取 .menu 文件，然后再通过 .menu 内指定的内容去实时读取文件。（称为热加载）
5. 因此我们可以通过在启动游戏前就准备好相关文件，来使用热加载机制。

**热加载方法**
1. 在游戏运行过程中，你可以直接修改以下几种文件，而不需要重启游戏：
   - `.menu` 文件（部分内容无法热加载）
   - `.mate` 文件
   - `.model` 文件
   - `.tex`文件（如果你装了缓存插件，那就不能热加载，建议通过 AccEX 插件修改）


2. 修改完成后：
   - 切换到游戏中的其他物品。
   - 再切换回来你的目标物品。
   - 游戏会读取修改后的最新内容。
  

**注意事项**
1. 部分内容无法通过热加载刷新：
   - .menu 文件中的物品图标数据无法热加载。（可以通过重新进入编辑模式来刷新，但个人不推荐这个办法）
   - .menu 文件中的物品名称和描述无法热加载。
   - 新增的文件无法通过这种方法直接加载，可能导致游戏出现 BUG。

2. 如果需要加载新增文件：
   - 使用 MaidLoader 的刷新功能，可以将新增文件加载进游戏。
   - 但不推荐使用，因为有时候加载了并不能生效，或是会出现其他问题。

通过以上方法，你可以高效地修改和测试 MOD，而无需频繁重启游戏。

## MOD 是如何加载的

其实游戏官方是有 MOD 支持的。

这个官方支持就是 `.mod`  格式的文件，只要把它放进 MOD 文件夹就可以生效。

不过这个 “官方支持” 并不算非常全面，许多高级需求（如覆盖已有文件、动态刷新等）必须通过其他办法才能实现。
<br>

所以呢出现了  [Modloader](https://github.com/Neerhom/COM3D2.ModLoader) 插件，现在已经不使用 `.mod` 格式的 MOD 了。

它直接拦截官方读取文件的函数，让游戏在访问文件系统时先检查 ModLoader 的目录与缓存，从而允许我们直接加载几乎任何官方物品格式的文件。(.menu .mate 之类的)

因此官方物品有什么功能，我们就可以使用什么功能，不用再使用官方功能受限的 `.mod` 格式。

因此做 MOD 的底层逻辑，其实就是对官方物品进行逆向，学习官方是怎么做的，从而做出自己的物体。

注：Modloader 也已经淘汰了，请使用 [MaidLoader](https://github.com/Pain-Brioche/COM3D2.MaidLoader) 它们的基础功能是一样的，但是 MaidLoader 更强大。

更详细的信息请参考
 - [https://github.com/Neerhom/COM3D2.ModLoader](https://github.com/Neerhom/COM3D2.ModLoader)
 - [https://github.com/Pain-Brioche/COM3D2.MaidLoader](https://github.com/Pain-Brioche/COM3D2.MaidLoader)

<br>

不过呢其实，在 [CM3D2 v1.11](https://www.kisskiss.tv/cm3d2/update.php) 版本，官方就添加了可以从 MOD 文件夹中直接读取 `*.menu,*.model,*.mate,*.anm,*.tex` 的能力

所以部分 MOD 其实不需要 Modloader 也能读取

![图片](https://github.com/user-attachments/assets/326ab08f-1f6c-419f-83b5-580182a77553)

<details>

<summary>Unity 修改届背后的男人</summary>

如果你在任意工具链往下挖掘，你会发现几乎所有基础代码都是由 https://github.com/ghorsington 创建的（https://github.com/denikson）

包括 BepinEX、UmaiUme、COM3D2.i18nEx 、CM3D2.MaidFiddler、CM3D2.YATranslator、IMGUITranslationLoader 等

都是马男为 COM3D2 创建的……

我们的马男为了玩 COM3D2 创建了整个工具链，太强大了马男

而如今 BepinEX 等工具广泛用于其他游戏，包括隔壁的 ILLUSION。

</details>





## 对官方物品进行修改

### 提取官方物品

以官方的 dress118_stkg_i_.menu 为例

#### 找到文件名

方法 1 ：按 Shift + I 打开 PropMyItem InoryS 版

在袜子栏搜索 118，我有这么多是因为我有 MOD

![图片](https://github.com/user-attachments/assets/abc4759c-9b2f-4d25-9235-18bd5d07e79a)

装备上后在控制台可以看见这个物品的 menu 名称（只有 InoryS 版才会显示）

方法 2：在安装 SybarisArcEditor（在英文工具包里） 的情况下，在编辑模式一起按下 M O D 三个键，左上角就会有一个导出，此时装备一个物品，然后点导出，就能看到文件名。

方法 3：用 AccEX 插件（F12）点导出时也会显示文件名.

#### 提取文件

由于是官方物品，我们需要使用 SybarisArcEditor（在英文工具包里）  从游戏文件内提取这个袜子的相关文件

如果你没安装，把 SybarisArcEditor.exe 放到 COM3D2.exe 旁边就行了

![图片](https://github.com/user-attachments/assets/68c9f72a-2dcc-4dc6-80ad-0bcdbd06deec)

打开后会很卡，耐心等一会

然后你会发现 dress118_stkg 什么都搜不到

那是因为这是从 CM3D2 联动过来的，这就是为什么有的东西你找不到

去 CM3D2 那边打开 SybarisArcEditor（如果你没安装，把 SybarisArcEditor.exe 放到 CM3D2.exe 旁边就行了）

可以看到官方文件种类和 dlc 名称进行了分类

![图片](https://github.com/user-attachments/assets/9cc53d34-156c-4126-8d79-4582741b7d85)

依次点开，你会发现有 .mate .menu .model 和几个 .tex

依次右键，点保存

得到以下几个文件，还记得之前说的组成吗？

![图片](https://github.com/user-attachments/assets/6ae375de-212f-4868-9ae8-7127e42d9939)

### 修改官方物品

很久以前， KISS 官方推出了 .mod 格式，现在已经淘汰了

随着 Modloader 和 MaidLoader 的出现，它允许我们直接以官方物品的格式来加载物品，因此官方有什么功能，我们就可以使用什么功能。

<br>
.menu 其实就是个 txt 文件，只不过内部要遵照一定的格式

所以我们需要一些功能，在目录的 English Modding Tools Pack 里面的 Core Modding Tools (English)，有各种工具

#### menu

用工具转成 txt 或用编辑器打开 .menu

这里用我自己做的 menu 编辑器打开，本来我都是用某 D 的工具，但是他禁止外国人使用，不好分发。

为了大家有相对好用的工具，只好自己做了

![图片](https://github.com/user-attachments/assets/fc89861f-debb-47e4-bb63-54e443bf35e6)

可以看到 menu 的基本组成
<br>

menu 文件详细请参附录，或 https://seesaawiki.jp/com3d2mod_wiki/d/menu

<br>

我们把东西都改个名，比如都改成 learn

注意文件名不能以 mod 开头，不然你会发现它读不了

(MODフォルダにMODファイルが見つかりません。)

<details>

<summary>因为和官方 .mod 格式冲突</summary>

![图片](https://github.com/user-attachments/assets/ca35929d-6630-4777-a730-a67512fc630a)

![图片](https://github.com/user-attachments/assets/e85738d9-84f6-4f17-bddc-b0989d26d02c)

</details>



![图片](https://github.com/user-attachments/assets/b278da2a-8430-4f6b-a1d1-64f55c8b9528)


<br>

然后打开 menu 编辑，编辑指向对应文件

![图片](https://github.com/user-attachments/assets/b3895ac4-c11a-4f96-8a8a-c95e5553a4d0)

#### mate

那么你会问其他的 2 个 .tex 是在哪里指定的？

答案是，可以在 .model 或 .mate 里指定

.mate 可有可无，如果你指定了 .mate，那么就会覆盖 .model 里面指定的内容（所以可以通过添加多个 .meun 和 .mate 组合来制作换色 mod 而不需要修改 .model）

这个官方物品使用了 .mate 所以我们这里主要关注 .mate 文件，.model 内的信息在第三课

<br>

用 mate 编辑器或者转成 txt 打开 .mate 文件

![图片](https://github.com/user-attachments/assets/ca1510ea-bd92-4eb7-97df-4412c215dfe5)

改成对应贴图名字，但不带 .tex

那个路径没什么用，可以忽略，随便填个东西就行了(COM3D2 2.06 +)

![图片](https://github.com/user-attachments/assets/f849350f-f2fe-4de6-9974-64b36b1b743f)

<br>

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

<br>

恭喜你已经学会了 MOD 的基本组成

### 对别人的 MOD 进行修改

同理，只不过不需要提取了罢了

使用 ShiftClickExplorer 插件，在编辑模式 shift 右键物品，就可以直接转跳到目标文件。

文件都是见首页

## 使用 AlwaysColorChangeEx

我们可以使用 AlwaysColorChangeEx 轻松完成刚刚的操作和编辑 mate，文件都是见首页

默认快捷键 F12

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


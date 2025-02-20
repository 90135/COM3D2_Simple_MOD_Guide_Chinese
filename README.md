# COM3D2 简明 MOD 教程

基于案例教学，从原理明白为什么（大概吧）

<br>

个人水平有限，如有错误还恳请各位斧正

<br>

本文档是开源的，欢迎贡献

<br>

欢迎提问，加群或者使用 Issue 或 Discussions

<br>

我建议你完整阅读教程，因为案例教学会有很多知识点散落其中，比如：骨骼跟随原理、以任意姿势导出、为什么表面是黑的……

包括附录中也有很多知识，别忘了。

## 阅读地址

图片直接上传到 github，加载慢/加载不了请自备上网工具。

建议访问 gitbook 获得更佳阅读体验：

[https://90135.gitbook.io/com3d2_simple_mod_guide_chinese](https://90135.gitbook.io/com3d2_simple_mod_guide_chinese)

<br>

或者你也可以直接点本仓库里的 .md 文件阅读，项目地址：

[https://github.com/90135/COM3D2_Simple_MOD_Guide_Chinese](https://github.com/90135/COM3D2_Simple_MOD_Guide_Chinese)

## 目录

 - [附录，有很多知识哟](https://90135.gitbook.io/com3d2_simple_mod_guide_chinese/fu-lu)
 - [第 1 课，MOD 的组成和使用 AlwaysColorChangeEx 插件制作简易换色](https://90135.gitbook.io/com3d2_simple_mod_guide_chinese/di-1-ke-mod-de-zu-cheng-he-shi-yong-accex-cha-jian-zhi-zuo-jian-yi-huan-se)
 - [第 2 课，初次修改模型之简易修改袜子穿模](https://90135.gitbook.io/com3d2_simple_mod_guide_chinese/di-2-ke-chu-ci-xiu-gai-mo-xing-zhi-jian-yi-xiu-gai-wa-zi-chuan-mo)
 - [第 3 课，移植小物件之特定于妹抖的东西](https://90135.gitbook.io/com3d2_simple_mod_guide_chinese/di-3-ke-yi-zhi-xiao-wu-jian-zhi-te-ding-yu-mei-dou-de-dong-xi)
 - [第 4 课，用形态键或 .anm 让物品动起来](https://90135.gitbook.io/com3d2_simple_mod_guide_chinese/di-4-ke-yong-xing-tai-jian-huo-anm-rang-wu-pin-dong-qi-lai)
 - [第 5 课，做一双 HighHell 插件高跟鞋](https://90135.gitbook.io/com3d2_simple_mod_guide_chinese/di-5-ke-zuo-yi-shuang-highhell-cha-jian-gao-gen-xie)

## 交流群

欢迎提问

 - QQ 967954608 加群暗号 MOD
 - Discord https://discord.gg/XQVfcJWbPp

## 用到的工具

### 上网工具

- 自备
 - 没有上网工具基本寸步难行

### MOD 工具
 - English Modding Tools Pack 英文改装工具包
   - [https://discord.com/channels/297072643797155840/865160223118196737/871444415498031145](https://discord.com/channels/297072643797155840/865160223118196737/871444415498031145)
   - [https://www.mediafire.com/file/na4751q6nctytpx/%5BCOM3D2%5DEnglish_Mod_Tools_Pack_2.20.2024.zip/file](https://www.mediafire.com/file/na4751q6nctytpx/%5BCOM3D2%5DEnglish_Mod_Tools_Pack_2.20.2024.zip/file)
  
 - 本人编写的 MOD 制作工具
   - [https://github.com/90135/COM3D2_MOD_EDITOR](https://github.com/90135/COM3D2_MOD_EDITOR)
     
### Blender 相关

Blender 是一个开源的建模软件

 - Blender 
   - 推荐 3.3.21 版本
   - 如果你要编辑 lobody highpoly 体型那种高顶点数模型，用 3.3 太卡的话，可以用 2.39.18，但是会有一些 bug，所以编辑完后要导回 3.3.21 再进行一些处理
   - 3.6 版本也能勉强使用，不过会有一些 BUG，比如有的功能没有
   - [https://download.blender.org/release/](https://download.blender.org/release/)
   - [https://download.blender.org/release/Blender3.3/blender-3.3.21-windows-x64.zip](https://download.blender.org/release/Blender3.3/blender-3.3.21-windows-x64.zip)
  
 - Blender COM3D2 插件
   - 2.39.18 使用 luv.2022.09.16
   - 3.3.21/3.6 使用最新版 (luv.2023.09.23)
   - [https://github.com/luvoid/Blender-CM3D2-Converter/releases](https://github.com/luvoid/Blender-CM3D2-Converter/releases)

 - Blender MMD 插件
   - 3.3.21 使用 2.8.1 版本
   - [https://github.com/UuuNyaa/blender_mmd_tools/releases](https://github.com/UuuNyaa/blender_mmd_tools/releases)

#### Blender 教程

 - 先看这个速成一下，时间比较短
   - [https://www.bilibili.com/video/av355541649](https://www.bilibili.com/video/av355541649)

 - Blender 界面介绍
   - https://www.bilibili.com/video/av113832639136668

 - UV 和材质教程
   - [https://www.bilibili.com/video/av385242165](https://www.bilibili.com/video/av385242165)
   - https://www.bilibili.com/video/av926436454
   - https://www.bilibili.com/video/av950602700

 - 比较系统的课
   - [https://www.bilibili.com/video/av112852916568795](https://www.bilibili.com/video/av112852916568795)
   - [https://www.bilibili.com/video/av218387890](https://www.bilibili.com/video/av218387890)

 - 辣椒酱系统课（太细致了，需要深入 Blender 时看）
   - [https://www.bilibili.com/video/av205836298](https://www.bilibili.com/video/av205836298)


### 游戏插件相关
  
 - AlwaysColorChangeEx，简称 AccEX （MOD 制作工具）
   - [https://github.com/90135/COM3D2_Simple_MOD_Guide_Chinese/tree/main/%E7%B4%A0%E6%9D%90%E5%8C%85](https://github.com/90135/COM3D2_Simple_MOD_Guide_Chinese/tree/main/%E7%B4%A0%E6%9D%90%E5%8C%85)

 - ShaderServant（额外着色器支持插件）
   - [教程](https://github.com/90135/COM3D2_Simple_MOD_Guide_Chinese/blob/main/%E9%99%84%E5%BD%95/ShaderServant%20%E5%92%8C%20MaterialEditor%20%E7%9A%84%E5%AE%89%E8%A3%85.md)
   - [https://github.com/krypto5863/COM3D2.ShaderServant](https://github.com/krypto5863/COM3D2.ShaderServant)

 - MaterialEditor（类似 AccEX 的工具，但支持额外着色器）
   - [教程](https://github.com/90135/COM3D2_Simple_MOD_Guide_Chinese/blob/main/%E9%99%84%E5%BD%95/ShaderServant%20%E5%92%8C%20MaterialEditor%20%E7%9A%84%E5%AE%89%E8%A3%85.md)
   - [https://discord.com/channels/297072643797155840/736350853442699284/1318388889169166336](https://discord.com/channels/297072643797155840/736350853442699284/1318388889169166336)

 - PropMyItem，Inory-S 版（随时随地呼出物品菜单）
   - 比其他版本多了个查看 accVag 和 accAnl 分类的功能什么的
   - [https://github.com/InoryS/COM3D2.PropMyItem.Plugin](https://github.com/InoryS/COM3D2.PropMyItem.Plugin)

 - ModItemExplorer（类似 PropMyItem，随时随地呼出物品菜单）
   - https://github.com/kidonaru/COM3D2.ModItemExplorer.Plugin

 - ShapekeyMaster（用于在游戏内调整形态键）
   - [https://github.com/krypto5863/COM3D2.ShapekeyMaster](https://github.com/krypto5863/COM3D2.ShapekeyMaster)
   - [https://github.com/InoryS/COM3D2.ShapekeyMaster](https://github.com/InoryS/COM3D2.ShapekeyMaster)  此版本可以（在启用 ShapeKey 条件时，在条件不满足时跳过 Shapekey 处理，以便其他插件可以使用）
 
 - ShapeAnimator（用于在游戏内调整形态键，老款）
   - [https://github.com/InoryS/COM3D2.ShapeAnimator.Plugin](https://github.com/InoryS/COM3D2.ShapeAnimator.Plugin)

 - LiveLink（使用此插件可以让你的游戏实时同步 Blender 中的姿态，做动画什么的可以实时预览，且可以实时发送网格变形什么的。）
   - [https://github.com/luvoid/COM3D2.LiveLink](https://github.com/luvoid/COM3D2.LiveLink)
  
 - PartEdit（用于在游戏内操作骨骼）
   - [https://ux.getuploader.com/com3d2_mod_kyouyu_f/download/107](https://ux.getuploader.com/com3d2_mod_kyouyu_f/download/107)

 - DynBoneEdit（用于编辑摇曳骨 .col .phy）
   - [https://ux.getuploader.com/trzr_tool/download/26](https://ux.getuploader.com/trzr_tool/download/26)

 - ShiftClickExplorer（编辑模式“shift+左键”物品转跳到 MOD 文件所在位置）
   - [https://github.com/krypto5863/COM3D2.ShiftClickExplorer](https://github.com/krypto5863/COM3D2.ShiftClickExplorer)

 - HighHeel-InoryS 版（高跟鞋插件）
   - [https://github.com/InoryS/COM3D2.HighHeel](https://github.com/InoryS/COM3D2.HighHeel)
  
 - BodyCategoryAdd（编辑模式添加身体类别，用于更换体型）
   - [https://ux.getuploader.com/cm3d2_k/download/88](https://ux.getuploader.com/cm3d2_k/download/88)

#### 错误处理插件
开发 MOD 时总会遇到错误，该装还得装

 - ExtendedErrorHandling（捕获错误，出现错误时不崩游戏，必装）
   - [https://github.com/krypto5863/COM3D2.ExtendedErrorHandling](https://github.com/krypto5863/COM3D2.ExtendedErrorHandling)

 - CatchUnityEventExceptions（确保unity订阅可以执行）
   - [https://github.com/BepInEx/BepInEx.Utility](https://github.com/BepInEx/BepInEx.Utility)

 - SuppressGetTypesErrorsPatcher（确保反射失败不会崩溃）
   - [https://github.com/BepInEx/BepInEx.Utility](https://github.com/BepInEx/BepInEx.Utility)

### 妙妙工具

 - Everything（全盘秒搜工具，还能搜文件内容什么的）
   - 建议开机启动，不然还要等索引
   - [https://www.voidtools.com/zh-cn/](https://www.voidtools.com/zh-cn/)
    
 - Bandizip（解压软件）
   - [https://cn.bandisoft.com/bandizip/](https://cn.bandisoft.com/bandizip/)

 - ScreenToGif（动图制作软件）
   - [https://www.screentogif.com/](https://www.screentogif.com/)

 - Photopea（在线版 PhotoShop）
   - [https://www.photopea.com/](https://www.photopea.com/)

### 素材相关

 - 本人的 MOD，可以当素材或者示例使用，可以随意修改分发
   - [https://mega.nz/folder/QRNxhRRZ#yuoWg3O9OLUHnOF1nwmLDw](https://mega.nz/folder/QRNxhRRZ#yuoWg3O9OLUHnOF1nwmLDw)

 - InoryS 的 MOD，可以当素材或者示例使用，可以随意修改分发（已获同意）
   - [https://mega.nz/folder/U6Jy0a6a#Pv5G9G_J5zoYc46TVmz6iA](https://mega.nz/folder/U6Jy0a6a#Pv5G9G_J5zoYc46TVmz6iA)

### 条款相关

  - KISS 条款
   - 发布 MOD 时需要遵守此条款，还需要在 MOD 内放置条款链接
   - [中文版](https://com3d2.jp/zh/cn/terms.html)
   - [日文版](http://kisskiss.tv/kiss/diary.php?no=558)
   - [英文版](https://com3d2.world/r18/modrul.html)

## MOD 发布
一般发布在 Twitter 上，带 #COM3D2 标签

这几个站点会爬取 Twitter 推文，有的站不会收录有裸露图像的推文，比如 motimoti。

相对来说 mukuu.herokuapp.com 会全一些，不过我比较喜欢 motimoti3d.jp。

   - [https://motimoti3d.jp/](https://motimoti3d.jp/)
   - [https://mods.meido.dev/](https://mods.meido.dev/)
   - [https://mukuu.herokuapp.com](https://mukuu.herokuapp.com)

## 其他参考资料
 - [https://seesaawiki.jp/com3d2mod_wiki/](https://seesaawiki.jp/com3d2mod_wiki/)
 - [https://seesaawiki.jp/com3d2_kaizou_info/](https://seesaawiki.jp/com3d2_kaizou_info/)
 - [https://discord.gg/custommaid](https://discord.gg/custommaid)
 - [https://github.com/luvoid/COM3D2-All-Bout-Bones](https://github.com/luvoid/COM3D2-All-Bout-Bones)

## 其他可以参考的教程
 - [zaj2001杂酱教程-图文](https://www.bilibili.com/video/BV1tu411R7TV/)
 - [ymk移植教程-图文](https://drive.google.com/drive/folders/1o0k9QREGKRmVlEr5WZSNUvBd7773ulN-)
 - [BDFFZI教程-视频](https://bdffzi-blog.pages.dev/posts/2633666094)
 - [BDFFZI教程-图文](https://www.bilibili.com/video/BV148411i7uy/)


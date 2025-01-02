# COM3D2 简明 MOD 教程

基于案例教学，从原理明白为什么（大概吧）

<br>

个人水平有限，如有错误还恳请各位斧正

<br>

本文档是开源的，欢迎贡献

## 阅读地址

建议访问 gitbook 获得更佳阅读体验。

[https://90135.gitbook.io/com3d2_simple_mod_guide_chinese](https://90135.gitbook.io/com3d2_simple_mod_guide_chinese)

或者你也可以直接点本仓库里的 .md 文件阅读

## 目录

 - [第 1 课，MOD 的组成和使用 AlwaysColorChangeEx 插件制作简易换色](https://90135.gitbook.io/com3d2_simple_mod_guide_chinese/di-1-ke-mod-de-zu-cheng-he-shi-yong-accex-cha-jian-zhi-zuo-jian-yi-huan-se)
 - [第 2 课，初次修改模型之简易修改袜子穿模](https://90135.gitbook.io/com3d2_simple_mod_guide_chinese/di-2-ke-chu-ci-xiu-gai-mo-xing-zhi-jian-yi-xiu-gai-wa-zi-chuan-mo)
 - [第 3 课，移植小物件之特定于妹抖的东西](https://90135.gitbook.io/com3d2_simple_mod_guide_chinese/di-3-ke-yi-zhi-xiao-wu-jian-zhi-te-ding-yu-mei-dou-de-dong-xi)
 - [第 4 课，用形态键或 .anm 让物品动起来](https://90135.gitbook.io/com3d2_simple_mod_guide_chinese/di-4-ke-yong-xing-tai-jian-huo-anm-rang-wu-pin-dong-qi-lai)

## 交流群

 - QQ 967954608 加群暗号 MOD
 - Discord https://discord.gg/XQVfcJWbPp

## 用到的工具

### MOD 工具
 - English Modding Tools Pack 英文改装工具包
   - [https://discord.com/channels/297072643797155840/865160223118196737/871444415498031145](https://discord.com/channels/297072643797155840/865160223118196737/871444415498031145)
   - [https://www.mediafire.com/file/na4751q6nctytpx/%5BCOM3D2%5DEnglish_Mod_Tools_Pack_2.20.2024.zip/file](https://www.mediafire.com/file/na4751q6nctytpx/%5BCOM3D2%5DEnglish_Mod_Tools_Pack_2.20.2024.zip/file)
  
 - 还有更好用的工具，比如 夜勤D ＠YakinKazuya 的工具，需要使用日本家庭 IP 访问，且禁止非日本人使用
   - [https://ykndsnest.work/yknDLoader/](https://ykndsnest.work/yknDLoader/)
  
 - 本人制作的简陋工具，未经大量测试，可能有 BUG
   - [https://github.com/90135/COM3D2_MOD_EDITOR](https://github.com/90135/COM3D2_MOD_EDITOR)
  
 - 本人的 MOD，可以当素材使用
   - [https://mega.nz/folder/U6Jy0a6a#Pv5G9G_J5zoYc46TVmz6iA](https://mega.nz/folder/U6Jy0a6a#Pv5G9G_J5zoYc46TVmz6iA)
     
### Blender 相关

 - Blender
   - 推荐 3.3.21 版本，如果你要编辑体型那种高模，3.3 太卡的话，可以用 2.39.18，但是会有一些 bug
   - [https://download.blender.org/release/](https://download.blender.org/release/)
   - [https://download.blender.org/release/Blender3.3/blender-3.3.21-windows-x64.zip](https://download.blender.org/release/Blender3.3/blender-3.3.21-windows-x64.zip)
  
 - Blender COM3D2 插件
   - 2.93.18 使用 luv.2022.09.16
   - 3.3.21 使用最新版 (luv.2023.09.23)
   - [https://github.com/luvoid/Blender-CM3D2-Converter/releases](https://github.com/luvoid/Blender-CM3D2-Converter/releases)

 - Blender MMD 插件
   - 3.3.21 使用 2.8.1 版本
   - [https://github.com/UuuNyaa/blender_mmd_tools/releases](https://github.com/UuuNyaa/blender_mmd_tools/releases)

### 插件相关
  
 - AlwaysColorChangeEx 插件，简称 AccEX （MOD 制作工具）
   - [https://github.com/90135/COM3D2_Simple_MOD_Guide_Chinese/tree/main/%E7%B4%A0%E6%9D%90%E5%8C%85](https://github.com/90135/COM3D2_Simple_MOD_Guide_Chinese/tree/main/%E7%B4%A0%E6%9D%90%E5%8C%85)

 - PropMyItem 插件，Inory-S 版（随时随地呼出物品菜单）
   - 比其他版本多了个查看 accVag 和 accAnl 分类的功能什么的
   - [https://github.com/InoryS/COM3D2.PropMyItem.Plugin](https://github.com/InoryS/COM3D2.PropMyItem.Plugin)

#### 错误处理插件
开发 MOD 时总会遇到错误，该装还得装

 - ExtendedErrorHandling（捕获错误，出现错误时不崩游戏，必装）
   - https://github.com/krypto5863/COM3D2.ExtendedErrorHandling

 - CatchUnityEventExceptions（确保unity订阅可以执行）
   - https://github.com/BepInEx/BepInEx.Utility

 - SuppressGetTypesErrorsPatcher（确保反射失败不会崩溃）
   - https://github.com/BepInEx/BepInEx.Utility

### 素材相关

 - 本人的 MOD，可以当素材或者示例使用
   - [https://mega.nz/folder/U6Jy0a6a#Pv5G9G_J5zoYc46TVmz6iA](https://mega.nz/folder/U6Jy0a6a#Pv5G9G_J5zoYc46TVmz6iA)


## 其他参考资料
 - [https://seesaawiki.jp/com3d2mod_wiki/](https://seesaawiki.jp/com3d2mod_wiki/)
 - [https://discord.gg/custommaid](https://discord.gg/custommaid)



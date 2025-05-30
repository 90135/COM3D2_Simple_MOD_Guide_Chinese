# 再见了所有的 NPRShader 插件

访问 gitbook 以获得更佳阅读体验：[https://90135.gitbook.io/com3d2_simple_mod_guide_chinese/fu-lu/shaderservant-he-materialeditor-de-an-zhuang](https://90135.gitbook.io/com3d2_simple_mod_guide_chinese/fu-lu/shaderservant-he-materialeditor-de-an-zhuang)

更换后如何玩场景 MOD：[https://90135.gitbook.io/com3d2_simple_mod_guide_chinese/com3d2_guide/ru-he-wan-chang-jing-mod-shaderservant-ru-he-wan-chang-jing](https://90135.gitbook.io/com3d2_simple_mod_guide_chinese/com3d2_guide/ru-he-wan-chang-jing-mod-shaderservant-ru-he-wan-chang-jing)

## 什么是 NPRShader 插件

NPRShader.Plugin 是一个添加额外着色器的插件，它往游戏内添加了自己同名的 NPRShader 着色器，且只能添加自己的 NPRShader 着色器。

但是这个插件无人维护、不开源、甚至停止分发，所以我们需要把它淘汰掉。

NPRShader 在 COM3D 2.38.0 中已经损坏，再次由于上述的原因，就连发个修复版修复都要偷偷摸摸的。所以不建议再使用了！

下图这个报错就是 NPRShader 炸了，并不是 COM3D2.HalfUnDressing.Plugin 干的

<img src="https://github.com/user-attachments/assets/b4cb8e29-aadc-437c-85a6-6865cc582b2d" width=500 />

## 什么是 ShaderServant

ShaderServant (ss) 是 NPRShader 的轻量级高性能替代品。 

它同时也是 npr_addition.cs (npra) 的替代品，如果有 MOD 要求 NPRShader 或者 npra，那么你只需要 ShaderServant 就够了。

<br>

ss 提供一个简单且非侵入式的外部着色器加载器，同时还支持旧的 NPR 标准。这意味着 NPR 材质无需任何编辑即可完美运行。

<br>

它是一个单纯的着色器加载器，不会有 GUI 什么的。（非常好的软件编写哲学之单一职责原则，使我的领结旋转）

简单来说就是这是一个着色器加载器，可以把额外的着色器加载进游戏内。

你可能听说过 NPRShader、liltoon 什么的，这些都是着色器。

只要有符合标准的着色器，它都能加载进游戏内。

## 什么是 MaterialEditor 

一个类似于 AlwaysColorChangeEX 的插件，允许你在游戏内实时查看材质效果。

可以替代之前 NPR 插件的 GUI。

它可以任意扩展，只要有着色器定义文件，就能显示。

而不是像 AlwaysColorChangeEX 或者 NPR 那样是硬编码的。

但是目前没有导出功能，所以对于模组作者来说目前只能预览效果，还需要手动填写 mate 文件。

目前只能在编辑模式使用，安装后在编辑模式左边会有一个 MaterialEditor 按钮，进入编辑器应该一眼就能看到。

注意，编辑材质后如果你保存了存档，那么你编辑的内容会关联到你的存档，下次读取时会自动加载编辑过的内容。


<img src="https://github.com/user-attachments/assets/e2607255-10e3-4c6a-9670-ae51fe5c26a5" width=500 />


<br>
<br>

# 更换成 ShaderServant 

如果你真的不知道，Github 下载一般在仓库主页右边的 Releases 标签中，点进去 Releases 后，在 Assets 标签中有下载；如果要下载整个仓库，点击仓库主页绿色的 Code 按钮，然后点击 Download ZIP。

如果你打算安装 MaterialEditor，可以跳过下载部分，因为 MaterialEditor 包内有这个。

1. 在你的文件夹里面搜索 `COM3D2.NPRShader.Managed.dll.`、`COM3D2.NPRShader.Patcher.dll`、`COM3D2.NPRShader.Plugin.dll` 然后删除

2. 去这里下载 ShaderServant [https://github.com/krypto5863/COM3D2.ShaderServant](https://github.com/krypto5863/COM3D2.ShaderServant)

```
 给 COM3D2.5 使用的还没正式发布，需要到 Discord 下载
 先加入 Discord 频道：https://discord.gg/custommaid
 然后再打开：https://discord.com/channels/297072643797155840/736350853442699284/1370051971687518408
 不过你都用 2.5 了，我建议直接用 CMI：https://github.com/krypto5863/COM-Modular-Installer 会更可靠
```

4. 去这里下载 CM3D2.Serialization [https://github.com/luvoid/CM3D2.Serialization](https://github.com/luvoid/CM3D2.Serialization)
  
5. 解压 ShaderServant.zip 得到 COM3D2.ShaderServant.dll 放进 `COM3D2\BepInEx\plugins`

6. 解压 ShaderServant.zip 得到 ShaderServantPacks 文件夹，把 ShaderServantPacks 文件夹放进游戏根目录

7. CM3D2.Serialization.dll 放进 `COM3D2\BepInEx\plugins`


## 安装 MaterialEditor（可选）

不做 MOD，或者不自己修改材质可以不装。

插件没有快捷键，安装后在编辑模式左边会有一个 MaterialEditor 按钮。

目前 MaterialEditor 还没有正式发布，所以需要去 Discord 下载。

1. 加入 Discord 频道 [https://discord.gg/custommaid](https://discord.gg/custommaid)

2. 打开 [https://discord.com/channels/297072643797155840/736350853442699284/1318388889169166336](https://discord.com/channels/297072643797155840/736350853442699284/1318388889169166336)
    - 如果你是 2.5，到这里下载 [https://discord.com/channels/297072643797155840/736350853442699284/1370051971687518408](https://discord.com/channels/297072643797155840/736350853442699284/1370051971687518408)

4. 下载这两个包
    ![图片](https://github.com/user-attachments/assets/0e1d0393-d950-4ab8-a998-31c6b2a2972f)

5. 把 MaterialEditorDefinitions.zip 里面的 MaterialEditorDefinitions 文件夹放到游戏根目录

    ![图片](https://github.com/user-attachments/assets/c01e96ec-2191-4192-9b05-bc5ee120bd4e)
    
    ![图片](https://github.com/user-attachments/assets/1c0c73dd-756e-48ac-9763-9f9d825795d3)

6. 把 COM3D2.ME.zip 里面的 .dll 都放到 `COM3D2\BepInEx\plugins`
   
    （检查你之前也没有装过一样的，如果有，而且你不懂，建议覆盖）
   
    （这个包里的 ShaderServant 和 Github 上面的不一样，必须用这个版本）


8. 去这里下载 [https://github.com/Perdition-117/COM3D2.EditBodyLoadFix](https://github.com/Perdition-117/COM3D2.EditBodyLoadFix)

9. 把 COM3D2.EditBodyLoadFix.dll 放到 `COM3D2\BepInEx\plugins`


## ShaderServant 添加额外着色器

从 github 下载的 ShaderServant 只自带 nprshaders 一种着色器，我们需要添加点额外的。

1. 打开 [https://github.com/silver1145/scripts-com3d2](https://github.com/silver1145/scripts-com3d2)

2. 如图下载包

![图片](https://github.com/user-attachments/assets/663d7b10-309a-41d7-8dd8-8b5a5666c330)

3. 解压后找到如图文件夹

![图片](https://github.com/user-attachments/assets/d0f4f688-d446-46f9-9c6f-2e36d8bf810f)

4. 把 `Shaders` 文件夹里面的文件放进 `COM3D2\ShaderServantPacks`

![图片](https://github.com/user-attachments/assets/bf030b31-9ff7-48ff-b0e0-633ee62dbf94)

以后你有了新的着色器也是放进 `COM3D2\ShaderServantPacks` 文件夹就行了

## MaterialEditor 添加额外着色器定义

MaterialEditor 目前并不自带着色器定义，我们需要手动添加。

1. 打开 [https://github.com/silver1145/scripts-com3d2](https://github.com/silver1145/scripts-com3d2)

2. 如图下载包

![图片](https://github.com/user-attachments/assets/663d7b10-309a-41d7-8dd8-8b5a5666c330)

3. 解压后找到如图文件夹

![图片](https://github.com/user-attachments/assets/d0f4f688-d446-46f9-9c6f-2e36d8bf810f)

4. 把 `MaterialEditorDefinitions` 文件夹里面的文件放进 `COM3D2\MaterialEditorDefinitions`

![图片](https://github.com/user-attachments/assets/a7961056-700f-4c09-a1ff-a0c1f51584c2)

以后你有了新的着色器定义也是放进 `COM3D2\MaterialEditorDefinitions` 文件夹就行了

## 其他注意事项

1. 如果你在 `COM3D2\script` 文件夹里面有 `wrap_mode_extend.cs` 或 `wrap_mode_extend_npr.cs` 或 `wrap_mode_extend_sc.cs` 或 `WrapModeExtend.cs` 的话请删除， ShaderServant 自带 wrap mode extend 支持，否则你的材质会出问题。

2. 如果你在 `COM3D2\script` 文件夹里面有 或 `npr_addition.cs` 或 `npr_930_dpi_fix.cs` 的话请删除。

3. 如果你在 `Sybaris` 或 `UnityInjector` 或 `script` 里面有类似 EditBodyLoadFix 的插件，请删除。

## 其他方案

如果你真的想要类似 NPRShader 的 GUI

装一个 comsh，它有 NPRShader GUI。

不过安装比较复杂，我这里就不提供了。

地址在 [https://comsh.livedoor.blog/](https://comsh.livedoor.blog/)

右上角有个 googleドライブ （Google Driver）

# 安装完成应该这样


![图片](https://github.com/user-attachments/assets/e254f414-0b04-42bd-90b9-ec1288065fda)

其他 dll 略

![图片](https://github.com/user-attachments/assets/7a9408b7-9671-47ef-a3ef-9ad0ee01dceb)

![图片](https://github.com/user-attachments/assets/b47dba06-6c37-4a6a-92ad-24f66309f68b)

![图片](https://github.com/user-attachments/assets/9e761182-9958-4494-8c76-7aad6d64d82f)



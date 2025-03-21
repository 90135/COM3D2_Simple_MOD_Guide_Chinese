# 再见了所有的 NPRShader 插件

## 什么是 NPRShader 插件

NPRShader.Plugin 是一个添加额外着色器的插件，它往游戏内添加了自己的 NPRShader 着色器，且只能添加自己的 NPRShader 着色器。

但是这个插件无人维护、不开源、甚至停止分发，所以我们需要把它淘汰掉。

NPRShader 在 COM3D 2.38.0 中已经损坏，再次由于上述的原因，就连发个修复版修复都要偷偷摸摸的。所以不建议再使用了！

## 什么是 ShaderServant

ShaderServant 是 NPRShader 的轻量级高性能替代品。

提供一个简单且非侵入式的外部着色器加载器，同时还支持旧的 NPR 标准。需要澄清的是，这意味着 NPR 材质无需任何编辑即可完美运行。

它是一个单纯的着色器加载器，不会有 GUI 什么的。

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

<br>
<br>

# 更换成 ShaderServant 
1. 在你的文件夹里面搜索 `COM3D2.NPRShader.Managed.dll.`、`COM3D2.NPRShader.Patcher.dll`、`COM3D2.NPRShader.Plugin.dll` 然后删除

2. 去这里下载 ShaderServant [https://github.com/krypto5863/COM3D2.ShaderServant](https://github.com/krypto5863/COM3D2.ShaderServant)

    (给 COM3D2.5 使用的 还没正式发布，需要到这里下载 [https://discord.com/channels/297072643797155840/736350853442699284/1351258921179807877](https://discord.com/channels/297072643797155840/736350853442699284/1351258921179807877))

3. 去这里下载 CM3D2.Serialization [https://github.com/luvoid/CM3D2.Serialization](https://github.com/luvoid/CM3D2.Serialization)
  
4. 解压 ShaderServant 得到 COM3D2.ShaderServant.dll 放进 `COM3D2\BepInEx\plugins`

5. 解压 ShaderServant 把 ShaderServantPacks 文件夹放进游戏根目录

6. CM3D2.Serialization.dll 放进 `COM3D2\BepInEx\plugins`


## 安装 MaterialEditor（可选）

不做 MOD，或者不自己修改材质可以不装。

插件没有快捷键，安装后在编辑模式左边会有一个 MaterialEditor 按钮。

目前 MaterialEditor 还没有正式发布，所以需要去 Discord 下载。

1. 加入 Discord 频道 [https://discord.gg/custommaid](https://discord.gg/custommaid)

2. 打开 [https://discord.com/channels/297072643797155840/736350853442699284/1318388889169166336](https://discord.com/channels/297072643797155840/736350853442699284/1318388889169166336)

3. 下载这两个包
![图片](https://github.com/user-attachments/assets/0e1d0393-d950-4ab8-a998-31c6b2a2972f)

4. 把 MaterialEditorDefinitions.zip 里面的 MaterialEditorDefinitions 文件夹放到游戏根目录

![图片](https://github.com/user-attachments/assets/c01e96ec-2191-4192-9b05-bc5ee120bd4e)

![图片](https://github.com/user-attachments/assets/1c0c73dd-756e-48ac-9763-9f9d825795d3)

5. 把 COM3D2.ME.zip 里面的 .dll 都放到 `COM3D2\BepInEx\plugins` （检查你之前也没有装过一样的，如果有，而且你不懂，建议覆盖）

6. 去这里下载 [https://github.com/Perdition-117/COM3D2.EditBodyLoadFix](https://github.com/Perdition-117/COM3D2.EditBodyLoadFix)

7. 把 COM3D2.EditBodyLoadFix.dll 放到 `COM3D2\BepInEx\plugins`


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



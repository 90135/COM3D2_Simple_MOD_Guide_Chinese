在 `COM3D2/script` 里面的是由 BepInEx.ScriptLoader（ScriptLoader.dll） 加载的“脚本”（忽略 C# 不是脚本语言）。 

[https://github.com/krypto5863/BepInEx.ScriptLoader](https://github.com/krypto5863/BepInEx.ScriptLoader)

该插件进行过 2 此不兼容更新，因此当你的游戏报错：

```
Skipping loading `...` because it references outdated HarmonyWrapper and BepInEx.Harmony. To fix this, refer to github.com/denikson/BepInEx.ScriptLoader#upgrading-to-1240.
```

或

```
error cs0619: HarmonyLib.Harmony.UnpatchAll(string)' is obsolete Use Unpatchself() to unpatch the current instance.
```

时，你需要手动修复你的脚本，别紧张，这很容易。


### 更新

如果你不知道你的 ScriptLoader 是什么版本，建议直接更新到最新版。

[https://github.com/krypto5863/BepInEx.ScriptLoader](https://github.com/krypto5863/BepInEx.ScriptLoader)

到这里下载，然后把  ScriptLoader.dll  放到 `COM3D2\BepInEx\plugins`

### 修复

使用任意文本编辑器打开脚本 (`COM3D2/script` 内的 .cs 文件)


1. 将脚本内的 `HarmonyWrapper.PatchAll` 替换为 `Harmony.CreateAndPatchAll`
2. 将脚本内的 `Harmony.UnpatchAll(string)` 替换为 `Harmony.UnpatchSelf()`

有时候前缀可能不是 Harmony ，而是  `instance.UnpatchAll();` 之类的 也是一样替换为 `instance.UnpatchSelf()`

修改前

![图片](https://github.com/user-attachments/assets/560c1850-5e8c-47b6-8de3-71e5f6e0792b)

修改后

![图片](https://github.com/user-attachments/assets/d4329331-ed57-4404-af07-1a0f0d8005c0)




### 其他

此外，如果有一个脚本出错，那么插件加载器会拒绝加载所有脚本。

但给的报错往往不是罪魁祸首。

一般而言是报错的那个脚本的上一个（字母顺序）

如果不是，请一个个禁用尝试

比如把 `test.cs` 改成 `test.cs.dis`

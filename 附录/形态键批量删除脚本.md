mute 就是静音，就是取消打勾

![图片](https://github.com/user-attachments/assets/5241fb7d-8033-4348-b64e-fdd60884c16b)



## 如何使用

选中你想修改的网格，最好是物体模式

然后切换到 scripting 模式，点新建

![图片](https://github.com/user-attachments/assets/9b8c8f57-fe84-44ee-86ef-c1b4dcf5fb9a)

粘贴下面的脚本并执行

## 工作流


### 如果你想批量删除不想要的形态键 选项 A
1. 手动 mute 需要的形态键
2. 使用 `反转形态键的 mute 状态` 脚本
3. 使用 `删除所有 mute 的形态键` 脚本

### 如果你想批量删除不想要的形态键 选项 B
1. 使用 `mute 所有形态键` 脚本
2. 手动取消 mute 想要的形态键
3. 使用 `删除所有 mute 的形态键` 脚本



## 脚本

### 反转形态键的 mute 状态：
```
import bpy

# 获取当前选中的对象
obj = bpy.context.active_object

# 确保对象存在并具有形态键
if obj and obj.data.shape_keys:
    shape_keys = obj.data.shape_keys.key_blocks
    for shape_key in shape_keys:
        # 反转形态键的 mute 状态
        shape_key.mute = not shape_key.mute
        print(f"Shape Key '{shape_key.name}' mute状态已切换为: {shape_key.mute}")
else:
    print("选中的对象没有形态键或没有选中对象。")
```




### mute 所有形态键：
```
import bpy

# 获取当前选中的对象
obj = bpy.context.active_object

# 确保对象存在并具有形态键
if obj and obj.data.shape_keys:
    shape_keys = obj.data.shape_keys.key_blocks
    for shape_key in shape_keys:
        # 设置 mute 为 True
        shape_key.mute = True
        print(f"Shape Key '{shape_key.name}' 已被 mute.")
else:
    print("选中的对象没有形态键或没有选中对象。")

```


### 删除所有 mute 的形态键：
```
import bpy

# 获取当前选中的对象
obj = bpy.context.active_object

# 确保对象存在并且具有形态键
if obj and obj.data.shape_keys:
    # 获取形态键列表
    shape_keys = obj.data.shape_keys
    key_blocks = shape_keys.key_blocks
    
    # 收集需要删除的形态键名称，但跳过基础形态键 Basis
    keys_to_delete = [key_block.name for key_block in key_blocks  if key_block.mute and key_block.name != "Basis"]
    
    # 删除静音状态的形态键
    for key_name in keys_to_delete:
        obj.shape_key_remove(key_blocks[key_name])
    
    print(f"已删除 {len(keys_to_delete)} 个静音状态的形态键。")
else:
    print("当前选中的对象没有形态键。")
```

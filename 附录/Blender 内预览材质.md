在我们把材质转换为 COM3D2 材质以后

你会发现默认状态下无法预览材质，都会显示为粉色

![图片](https://github.com/user-attachments/assets/403bb7a8-9184-4d23-909c-bdab0b885bb0)



我们来到 shading 模式

在这里选择对应的贴图，然后你会发现还是怪怪的

![图片](https://github.com/user-attachments/assets/a60fb13e-6901-425c-8c3b-c840429379ec)

这个始终是 CM3D2 Converter 插件模拟的，不能完全代表游戏内渲染

所以我们还是直接把 CM3D2 shader 的线断开，然后把贴图拖进来（不能读 tex，转成图片再拖），直接连到材质输出比较方便

![图片](https://github.com/user-attachments/assets/4e3374b4-da2d-4c5b-91e1-a6535811cf98)


当然你也可以添加个别的着色器，然后再连

![图片](https://github.com/user-attachments/assets/4ecde56c-4f28-469e-b00c-8e0fbc66fbc7)


<br>
<br>

**当然，再次强调，在这里调的任何东西都与游戏效果内没有任何关系**

只有保存到 .model 中的东西才会对游戏产生影响

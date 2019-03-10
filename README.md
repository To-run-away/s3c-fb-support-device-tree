# s3c-fb-support-device-tree
4.x的内核绝大多数驱动都是支持设备树方式传递参数的。这样对于绝大多数gpio的操作
都可以不用驱动工程师来实现。
三星目前可能不打算维护s3c-fb.c的文件了，而一直在支持DRM方式的驱动，所以原始的
2.x，3.x内核使用的framebuffer驱动就不能用了（除非自己打算写platform_device，
gpio之类的初始化）。

本项目是自己学习设备树的一个简单使用。使用的是s5pv210处理器,九鼎的X210开发板。

接口说明:
1.LCD的供电使用GPD0引脚,默认低电平LCD供电(GPD0也可以支持pwm0调节背光亮度,这里暂时没使用)
2.24个数据引脚和芯片手册一致。
3.DCLK,VSYNC,HSYNC和DCLK和芯片手册给的一致。
4.芯片的SYS_OE引脚接的是给LCD芯片的供电使能引脚,需要设置为高电平或者SYS_OE状态。


本驱动支持两种probe方式,一种是通过之前的id_table方式,一种是设备树的of_device_id 方式。
在定义S3C_FB_OF宏的情况下是支持设备树方式,没定义这个宏是支持id_table方式。
默认是早probe函数前面定义了这个S3C_FB_OF宏的。





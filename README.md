# 程序环境部署
1. 为了确保程序能在您的机器上运行，请确保您的机器上安装了Linux、Qt(版本>5.0)、opencv
2. 如果您的opencv安装环境不是默认路径的话，请在.pro文件中重新配置好您的opencv安装路径
3. 项目所使用的相机为uvc相机，请确保您的相机支持UVC协议
# 程序控制功能开启
为了确保程序适应多种开发环境，而不是仅仅局限于龙芯2k1000开发板上，
我们将仓库中程序关于控制的部分关闭了！！！
如果需要打开的话，可以通过修改"dealClass.h"文件中的代码来启动,
如下所示
```
class dealClass{
public:
......
......
const static bool isControl = true;
......
......
};
```
**注意打开控制功能一定要确定是否具备相应的io口以及pwm**
**io及pwm可以在widget.cpp中widget的构造函数中查看**
```
Widget::Widget(QWidget *parent) :
    QWidget(parent),
    ui(new Ui::Widget)
{
......
......
        gpioValve = new controlGPIO(37);//阀门
        gpioLamp = new controlGPIO(38);//灯光报警
        pwmGas = new controlPWM(1);//气泵
        pwmGas->set_duty(0);
......
......
}
```

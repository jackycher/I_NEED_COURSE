##北理工抢课专用程序

#免责声明

1. 抢课是一种很不好的行为，因为你能抢到课，就说明有人退课。退课很有可能是为了在主观上把课让给同学、男/女朋友。
2. 抢课归根结底抢的是一种稀缺资源，技术壁垒能够左右资源的再分配，从进化论的角度或许合理，但是否觉得公平，还是要因人而异。
3. 我的课都选好了，所以并不需要这个工具，所以发布这个工具只是为了交流技术。
4. 抢课会给服务器带来刷新压力，所以请把刷新时间拉长一些。
5. 我只是个做工具的，把工具给你了，怎么用就看你了。
6. 如果你用了这个工具，就说明你愿意承担一切后果，而不要赖到作者头上。
7. 随手写的小程序，连代码加文档加下载环境也没花几分钟，所以有BUG别骂我，不保证对每个人都好使。
8. 写文档水平太差，请发动你们的洪荒之力好好理解，理解不了也别问我了。。
9. 抢上课了就好好学习吧，以后自己写脚本。
10. 人生苦短，我用Python

##程序功能

不间断刷新课程列表，自动抢能够抢到的课。建议用法：把这个程序开着，让他跑着吧，抢上课了就会自动停的吧？我不确定。。。。

##程序环境

Python2.7

##依赖库 （应该都是自带的标准库，装了python就都有了）

1. urllib
2. re
3. time
4. sys
5. json 

##用法

python i_need_course.py 超时时间（秒） 配置文件名

例如

python i_need_course.py 1 0700015.configure.txt

## 关于配置文件

由于目前这个系统，人和人之间提交的表单都不一样，我的解决方案是使用一个配置文件把表单的内容记录下来。每一门课都有一个配置文件。程序执行需要读取这个配置文件。配置文件如何获取？

1. 下载fiddler：https://www.telerik.com/download/fiddler 填email地址然后点download。
2. 进入选课界面
3. 打开fiddler
4. 对想要选的课，不管是不是已经满了，都点击“选课”按钮
5. 这时候fiddler里会多一条记录，URL地址应该是：http://grdms.bit.edu.cn/yjs/dwr/call/plaincall/YYPYCommonDWRController.pyJxjhSelectCourse.dwr
6. 点击这条记录，在右侧面板点击Inspectors，在弹出的下面的选项卡中选择Raw。
7. 把文本框中空行之后的部分复制到一个空文件中，文件名任选，保存到本程序的目录中。（具体需要复制的部分见本目录下的图片“configure.png”）
8. 这个文件名就是上面用法中的“配置文件名”
9. 除了需要配置文件之外还需要一个Cookie文件。

## 关于Cookie

程序还需要保存Cookie才能模拟你本人登录，得到Cookie的方法跟上面前6布一样，只不过这时候复制的内容不是空行以后的内容，而是以“Cookie: ”为开头的一行文本。（见图cookie.png）

这个文件必须命名为cookies.txt，保存到本程序目录下。

## 备注

1. Cookie文件一个人只需要一个，必须保存为cookies.txt。
2. 每一门课都需要一个配置文件，请不断重复上面的步骤。
3. 如果你想同时选多门课，那就同时抓取到多个配置文件，然后同时用多个控制台打开就好。（真·多进程）
4. 如果不会用，请参考代码推测用法……不负责一对一教学。
1、安装树莓派系统。
（1）下载树莓派系统并解压得到.img文件（树莓派下载地址：http://www.raspberrypi.org/downloads）
（2）格式化SD卡。使用SDFormatter.exe软件进行格式化。
（3）使用Win32DiskImager.exe将树莓派系统烧录到SD卡中。
参考链接：
http://www.waveshare.net/study/article-595-1.html 
http://jingyan.baidu.com/article/c14654139a12ad0bfcfc4c01.html

拷贝代码到桌面后：

2、自动启动程序
在终端使用nano进行编辑： sudo nano /etc/rc.local 
在exit 0 前插入 
sudo rm -rf /home/pi/Desktop/test.jpg
sudo python + 路径 + 代码 +&，如：python /home/pi/Desktop/PiCameraRig-master/run.py &

3、设置静态IP地址
若raspberrypi通过wifi连接，在终端输入：ip addr show查看IP地址
在终端使用root权限编辑：sudo nano /etc/network/interfaces
添加如下代码：
iface wlan0 inet static
address 192.168.1.12
netmask 255.255.255.0
gateway 192.168.1.255
若raspberrypi通过网线连接，则将wlan0改为eth0

4、其他设置。
1、在终端输入：sudo raspi-config，设置用户名和用户密码
2、在settings.json修改clientID和ip地址分别为用户名和服务器IP地址。

遇到的问题：
1、运行 python run.py时提示：No module named paho.mqtt.client
解决方法：安装paho.mqtt：在终端输入sudo pip install paho-mqtt 

2、运行 python run.py时提示：Camera is not enabled.Try running 'sudo raspi-config' and ensure that the camera has been enabled.
在终端输入 sudo raspi-config 设置pi camera 'enabled'

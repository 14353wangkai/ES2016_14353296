***
#实验四：配置安装ROS
该配置是基于Ubuntu15.10(或者Ubuntu16.04)
***
##第一步： 
&emsp;&emsp;
配置Ubuntu的仓库，对照<a href="https://help.ubuntu.com/community/Repositories/Ubuntu" >[1]</a>之后，下图处不同，虽然不是很清除干什么，但是还是照着改了。
![canonical](https://cloud.githubusercontent.com/assets/22441229/20085856/dd166efa-a5a6-11e6-89d5-940bbd6b6055.png)
这一步的目的是让我们的Ubuntu允许"restricted","universe","multiverse"三个条件
***
##第二步:
&emsp;&emsp;
   安装配置sources.list，利用命令<br>
&emsp;&emsp;
**sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'**
<br>
&emsp;&emsp;
*这个命令的意思大概就是将“deb ......"这个语句写入到ros-latest.list。 语句中lsb_release -sc代表的意思是版本名称，比如15.10就是Wily。 
<br>
配置完这一步之后，可以通过/etc/apt/sources.list.d'目录下的ros-latest文件中看到
![ros-latest](https://cloud.githubusercontent.com/assets/22441229/20086208/7ab8d66e-a5a9-11e6-98aa-91e3fd6490c5.PNG)
***
##第三步：
&emsp;&emsp;
设置口令，利用如下语句<br>
&emsp;&emsp;
**sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116**
<br>
&emsp;&emsp;该语句的意思是将Docker官方资料库的访问Key添加到自己的本地系统。
<a href="http://www.tuicool.com/articles/jIN7f27">[2]</a>
##第四步：
&emsp;&emsp;
安装，首先更新Debian包，利用语句<br>
 &emsp;&emsp;
**sudo apt-get update**
<br>
&emsp;&emsp;
然后谨记PPT忠告，只下载Desktop-Full,利用如下语句即可

 &emsp;&emsp;
 **1. sudo apt-get install ros-kinetic-desktop-full**

&emsp;&emsp;然后利用apt-cache search命令来找到可用的包，完整语句如下

&emsp;&emsp; **2. apt-cache search ros-kinetic**

##第五步：
&emsp;&emsp;对ROS进行初始化，使用如下命令：
<br>
&emsp;&emsp;
**1. sudo rosdep init**
<br>
&emsp;&emsp;
**2. rosdep update**

##第六步：
&emsp;&emsp;
设置环境变量，将setup.bash永久性地加入到环境变量中
<br>
&emsp;&emsp;
**1.echo "source /opt/ros/kinetic/setup.bash" >> ~/.bashrc**
<br>
&emsp;&emsp;
**2.source ~/.bashrc**
##第七步：
&emsp;&emsp;
利用apt-get安装rosintall工具<br>
&emsp;&emsp;
**sudo apt-get install python-rosinstall**<br>

&emsp;&emsp;
由于一开始没有截图，但是再次输入命令之后，可以看到下图提示，证明已经安装过了<br>
&emsp;&emsp;
![python-rosinstall](https://cloud.githubusercontent.com/assets/22441229/20086601/8a9cb37c-a5ac-11e6-8bc9-f8a56d52c7e3.PNG)
***
&emsp;&emsp;
指令到这里就完结了，配置完成。
***
本次遇到了一个问题:<br>
**问题**：再次输入sudo apt get install python-rosinstall 命令的时候，提示"can't locate ..."错误<br>
**解决**：后来才看到，自己一开始配置环境用的是source ...的临时配置方法，所以每次开启虚拟机之后都需要输入该命令，后来改成永久性的配置，就不需要如此麻烦了

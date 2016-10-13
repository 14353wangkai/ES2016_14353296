#配置DOL实验过程描述
###本次实验让我们配置了dol文件
***
DOL框架
<br>
&emsp;&emsp;
在应用接口方面：
定义了一些列计算和通信的过程，使得SHAPES平台可以使用一些分布式程序和并行化应用。这为程序员提供了方便，让他们不需要知道底层应用详细的知识就能进行编程。
<br>
&emsp;&emsp;
在函数测试方面：
为程序员们提供了同步测试代码的可能性。除了测试函数功能以外，这个框架还可以用于获取应用级别的性能参数
<br>
&emsp;&emsp;
在映射最优化方面：
目标是计算一个应用于SHAPES平台的最优化映射。
首先，基于XML的格式是允许用户在抽象层面去描述应用和结构信息的。并且，它包含了为了精确评估表现的信息。
***
<h2 align = "center">配置开始</h2>
<br>
##一：前期准备
<ol>
<li>将下图两个压缩包复制到ubantu中</li>
<img src="https://cloud.githubusercontent.com/assets/22441229/19222179/d93d3af4-8e84-11e6-8987-8dc683de5777.png"/>
<li>更换软件源，把US服务器改成china中的服务器</li>
<img src="https://cloud.githubusercontent.com/assets/22441229/19221372/c0859264-8e74-11e6-933f-e204c505636e.png"/>
<img src="https://cloud.githubusercontent.com/assets/22441229/19221393/3b2a519e-8e75-11e6-82d7-a6077052eef7.png"/>
<li>输入sudo apt-get update, 对ubantu进行更新同步</li>
</ol>

##二：安装必要软件
<ol>
<li>输入sudo apt-get install ant命令安装ant</li>
<li>输入sudo apt-get install openjdk-7-jdk命令安装jdk</li>
<li>输入sudo apt-get install unzip命令安装unzip</li>
</ol>
##三：解压dol_ethz和systemc-2.3.1
<ol>
<li>输入sudo mkdir dol，新建一个dol文件夹</li>
<li>然后，利用unzip命令sudo unzip dol_ethz.zip -d dol，将dol_ethz解压到上述压缩包中</li>
<li>使用tar命令sudo tar -zxvf systemc-2.3.1.tgz，将systemc-2.3.1解压</li>
</ol>

##四： 编译systemc
<ol>
<li>输入cd systemc-2.3.1进入systemc-2.3.1文件夹里面</li>
<li>输入sudo mkdir objdir在其中新建一个objdir的文件夹</li>
<li>输入cd objdir进入上述文件夹</li>
<li>输入sudo ../configure CXX=g++ --disable-async-updates进行配置，便于编译</li>
<li>输入sudo make install进行编译</li>
<li>编译完之后，输入cd ..退回systemc-2.3.1文件夹，再输入ls命令列出其中内容</li>
<li>输入sudo pwd记录当前路径</li>
</ol>
##五：编译dol
<ol>
<li>输入cd ../dol退回home，进入dol文件夹</li>
<li>利用gedit命令打开build_zip.xml的图形化界面，找到其中如下图所示的语句</li>
<img src="https://cloud.githubusercontent.com/assets/22441229/19221414/c6b22282-8e75-11e6-8a0f-66bd11f32855.png">
<br>
把它修改成
<br>
<img src="https://cloud.githubusercontent.com/assets/22441229/19221403/7d7ea446-8e75-11e6-98be-18f5b7e10ea6.png">
<br>
**黑框部分是第四大步第7小步中，pwd所得到的工作路径**

<li>输入sudo ant -f build_zip.xml all进行编译，编译成功之后会看到下图结果</li>
<img src="https://cloud.githubusercontent.com/assets/22441229/19221416/e1d4c240-8e75-11e6-916d-422c187be45a.PNG">
<li>最后，输入cd build/bin/main进入该文件夹，输入sudo ant -f runexample.xml -Dnumber=1运行其中一个例子之后，结果如下，证明成功~</li>
<img src="https://cloud.githubusercontent.com/assets/22441229/19221422/fd86777c-8e75-11e6-9d52-53b218a11bce.PNG">
</ol>
***
<h2 align = "center">配置完成</h2>
#实验感想
***
&emsp;&emsp;
本次实验是让我们配置DOL文件，图中我遇到了两个问题：
<ul>
<li> 问题：下载速度很慢，乃至以B/s为单位下载
<br> 解决：更换China类型的下载源即可，具体步骤如配置过程中所示
<li> 问题：不知道如何编辑build_zip.xml文件
<br> 解决：用gedit打开之后无法更改，修改文件必须在前面加上sudo命令才可以
</ul>
&emsp;&emsp;可能是运气比较好，除了换源之前折腾了半小时以外，基本没遇到什么大问题，所以花了一个小时左右配置好了，不过期间许多步骤都忘记截图了（重新配置了一遍又忘记了T_T）步骤描述的可能不是很清晰，实在抱歉。
<br>
&emsp;&emsp;不过无论如何，嵌入式实验的第一步算完成了~
***

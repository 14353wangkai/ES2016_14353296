#配置DOL实验过程描述
###本次实验让我们配置了dol文件
***
<h2 align = "center">配置开始</h2>
<br>
##一：前期准备
<ol>
<li>将下图两个压缩包复制到ubantu中</li>
<img src="yasuobao.png"/>
<li>更换软件源，把US服务器改成china中的服务器</li>
<img src="sources.png"/>
<img src="sources2.png"/>
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
<img src="before.png">
<br>
把它修改成
<br>
<img src="after.png">
<br>
黑框部分是16步中pwd所得到的工作路径

<li>输入sudo ant -f build_zip.xml all进行编译，编译成功之后会看到下图结果</li>
<img src="build.png">
<li>最后，输入cd build/bin/main进入该文件夹，输入sudo ant -f runexample.xml -Dnumber=1运行其中一个例子之后，结果如下，证明成功~</li>
<img src="running.png">
</ol>
***
<h2 align = "center">配置完成</p>

#配置DOL实验过程描述
###本次实验让我们配置了dol文件
***
<h2 align = "center">配置开始</h2>
<br>
##一：前期准备
<ol>
<li>将下图两个压缩包复制到ubantu中</li>
<img src="http://thumbnail0.baidupcs.com/thumbnail/a737986007cbf727ee528ee10611df29?fid=2133074088-250528-347392740943065&time=1475974800&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-gGF6K5ItHg3TjhrbB%2FR08Jwtn64%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=6549109488031701301&dp-callid=0&size=c710_u400&quality=100"/>
<li>更换软件源，把US服务器改成china中的服务器</li>
<img src="http://thumbnail0.baidupcs.com/thumbnail/c9b13d2ddf9c3714abd618bf5189aa7e?fid=2133074088-250528-97680347352384&time=1475974800&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-BPeILq35BYzH%2BURueOxbilpO0Tc%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=6549156920068737247&dp-callid=0&size=c710_u400&quality=100"/>
<img src="http://thumbnail0.baidupcs.com/thumbnail/ad1a65da806c670f5d02496e3e6aac0c?fid=2133074088-250528-835640450662546&time=1475974800&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-eN8cLlBji0uhh0Y4Y36%2Fv2AAPM0%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=6549171554829487425&dp-callid=0&size=c710_u400&quality=100"/>
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
<img src="http://thumbnail0.baidupcs.com/thumbnail/7255a0014b4fd513da3e99c0a24f6e4c?fid=2133074088-250528-80687256381029&time=1475974800&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-gOXkgEMcYiAxurUNLHo4RJDIx9E%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=6549191842193156960&dp-callid=0&size=c710_u400&quality=100">
<br>
把它修改成
<br>
<img src="http://thumbnail0.baidupcs.com/thumbnail/4ec2a5d69ac7ac2ce614efb4427df67a?fid=2133074088-250528-421738227187594&time=1475974800&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-OHi19DxDvQEsjQyBKU9vkbJ0MWo%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=6549199665685924137&dp-callid=0&size=c710_u400&quality=100">
<br>
黑框部分是16步中pwd所得到的工作路径

<li>输入sudo ant -f build_zip.xml all进行编译，编译成功之后会看到下图结果</li>
<img src="http://thumbnail0.baidupcs.com/thumbnail/ada7cd6508447e90bb90b9da945a5f85?fid=2133074088-250528-813373401006229&time=1475974800&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-XZ%2BwrqBoYWuOus20D4%2BRbSp3k78%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=6549210007101469975&dp-callid=0&size=c710_u400&quality=100">
<li>最后，输入cd build/bin/main进入该文件夹，输入sudo ant -f runexample.xml -Dnumber=1运行其中一个例子之后，结果如下，证明成功~</li>
<img src="http://thumbnail0.baidupcs.com/thumbnail/3b363b37630ac73860da030b9782a769?fid=2133074088-250528-456052073811159&time=1475974800&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-yMqRnsrxVeEDb1Fg0PHPHgz8ziI%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=6549217301874335787&dp-callid=0&size=c710_u400&quality=100">
</ol>
***
<h2 align = "center">配置完成</p>

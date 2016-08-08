# LearnCentOS
这个项目是我学习CentOS的一个记录

CentOS 6.8<br>
安装minimal版本。<br>
1、完成后配置网络。<br>
vi  /etc/sysconfig/network-scripts/ifcfg-eht0<br>
内容如下：<br>
DEVICE=eth0<br>
TYPE=Etherne<br>
tUUID=58d64342-6bca-4156-8d4b-3bb092190644<br>
ONBOOT=yes         //开机启动网络<br>
NM_CONTROLLED=yes<br>
BOOTPROTO=none<br>
HWADDR=00:15:5D:01:44:11<br>
IPADDR=192.168.1.103<br>
PREFIX=24<br>
GATEWAY=192.168.1.251<br>
DNS1=202.96.128.86<br>
DNS2=8.8.8.8<br>
DEFROUTE=yes<br>
IPV4_FAILURE_FATAL=yes<br>
IPV6INIT=no<br>
NAME="System eth0"<br>
2、安装编译器GCC和gdb<br>
yum list  gcc*<br>

yum install gcc.i686 gcc-c++.i686<br>
yum install gdb.i686<br>
其他常用工具安装如下<br>
yum -y install gcc gcc-c++ autoconf automake make<br>
yum -y install zlib zlib-devel openssl openssl--devel pcre pcre-devel <br>
<br>
<br>
3、安装git<br>
yum list  git*<br>
<br>
yum install git.i686<br>
4、编写C++代码编译测试<br>
vi test.cpp<br>
内容如下<br>
#include <iostream><br>
using namespace std;<br>

int main(void)<br>
{<br>
	cout<<"Hello World!"<<endl;<br>
}<br>
保存退出后编译<br>
g++ -o test test.cpp<br>
执行查看结果。<br>
./test<br>
出现Hello World!表示编译成功。<br>
5、安装nginx<br>
执行以下语句，<br>
rpm -ivh http://nginx.org/packages/centos/6/noarch/RPMS/nginx-release-centos-6-0.el6.ngx.noarch.rpm<br>
yum install nginx<br>
service nginx start<br>
      <br>
iptables -I INPUT 5 -p tcp --dport 80 -j ACCEPT<br>
    以上命令修改了/etc/sysconfig/iptables<br>
  <br>
6、配置Git服务器<br>
服务器上安装git<br>
<br>
<br>
增加git用户<br>
sudo useradd  git<br>

在/home/git/.ssh/下(如果没有.ssh目录，则 mkdir .ssh)<br>
touch authorized_keys<br>
把客户机的公钥拷贝到这个文件中，一个公钥一行。<br>

增加普通用户<br>
useradd jamie<br>
passwd jamie<br>
之后使用jamie用户<br>
初始化仓库<br>
sudo git init --bare sample.git<br>
修改仓库权限<br>
sudo chown -R git:git sample.git<br>
禁用shell登录<br>
编辑/etc/passwd<br>
git:x:1001:1001:,,,:/home/git:/bin/bash<br>
改为：<br>
git:x:1001:1001:,,,:/home/git:/usr/bin/git-shell<br>
这样，git用户可以正常通过ssh使用git，但无法登录shell，因为我们为git用户指定的git-shell每次一登录就自动退出。<br>
现在，可以通过git clone命令克隆远程仓库了，在各自的电脑上运行：<br>
$ git clone git@server:/srv/sample.git<br>
<br>
<br>


当我们使用sudo命令切换用户的时候可能会遇到提示以下错误：xxx is not in the sudoers file. This incident will be reported，xxx是你当前的用户名，究其原因是用户没有加入到sudo的配置文件里<br>
切换到root用户，运行visudo命令<br>
在打开的配置文件中，找到root ALL=(ALL) ALL，在下面添加一行<br>
xxx ALL=(ALL) ALL 其中xxx是你要加入的用户名称<br>
输入:wq保存并退出配置文件，再次使用sudo命令就不会有上面的提示了。<br>
<br>


CentOS <br>
yum install gcc <br>
yum info gcc <br>
yum remove gcc <br>
yum list gcc* <br>
<br>
/etc/yum.conf 配置文件<br>
尽量使用yum维护软件包，不要使用rpm，因为rpm命令完整性检查需要自己做。<br>

yum grouplist //查看所有语言包列表<br>

yum groupinstall ‘Chinese Support’ //安装中文字体<br>

'#'提示符为超级用户<br>
$提示符为普通用户<br>
默认情况下 linux有一个图形界面 alt +f1和五个文本登录界面alt + f[2-6]<br>

shift pgup  在文本界面回看上一屏幕<br>
id 命令 查看当前用户信息<br>
ctrl d退出当前用户<br>
sudo  临时使用root用户操作<br>
visudo 配置sudo<br>

linux bash默认shell<br>
history  历史命令查看<br>
!28    执行历史中28号指令<br>

/proc   内存中系统文件<br>
/sys   内存中<br>
/var   一般存放数据<br>

l.   只显示隐藏文件<br>
ls -d */   //显示所有目录<br>
ls -ld 目录     查看目录本身，不进入里面查看<br>

du -sh   统计目录大小<br>

df -Th    显示文件系统，-T 显示类型。<br>

file a   文件类型。<br>
tab 键自动补齐命令或文件名。<br>

ctrl c  清除命令行。<br>

vim中<br>
:e  重新读取文件。不保存修改。<br>
vi 可以同时打开多个文件，<br>
使用:n显示下一个，:N显示上一个文件<br>
:wq  :w  :x  :q  :q!<br>
G  最后一行<br>
gg 第一行<br>
:1000   到1000行<br>
/new   搜索new <br>
n到下一个 N 回去一个<br>
:nohl    取消高亮<br>
3yy  复制行<br>
p  粘贴<br>
dd  剪切<br>
ctrl v  块选择模式,支持列模式<br>
u  恢复操作到上一次。后悔<br>
ctrl r 反后悔<br>

ctrl-w ,s 分窗口<br>
set nu 增加行号  <br>
set nonu  取消行号<br>
set ai  自动缩进<br>
可以编辑~目录下的.vimrc<br>
   set number<br>
%s/X86_64/i386/g      全文搜索且替换。go<br>
   
文件权限<br>
file：<br>
r    read<br>
w    write<br>
x    exe<br>
dir：<br>
r    ls<br>
w    rm rmdir touch<br>
x   ls -l<br>
chown  改变文件的拥有者<br>
chgrp  改变文件所属组<br>
chmod g+w   u,g,o=a   +,-  r,w,x<br>
chmod 640         <br>
安全相关文件<br>
/etc/passwd    用户信息<br>
/etc/shadow    密码信息<br>
/etc/group     组信息<br>
新建用户会把 /etc/skel/目录中的文件拷贝到新建用户主目录中。<br>
用户环境初始化文件<br>
~/.bash_profile   登录前要做什么<br>
~/.bashrc         同上<br>
~/.bash_logout    登出后要做什么<br>
可以再登录前自定义命令<br>
cat ~/.bashrc<br>
alias l=‘ls -al’<br>
useradd   增加用户<br>  
userdel   删除用户<br>
usermod   修改用户<br>

. 或者 source scriptname  立即执行脚本<br>
密码规则<br>
/etc/login.defs   新用户默认的权限定义在这里<br>

特殊目录权限<br>

chmod  u+t  例如/tmp目录  是说每个人都可以再这里读写操作，单是只限制自己的文件。<br>
chmod g+s ti  协同工作目录。同组都能访问。<br>

可以使用acl微调用户权限<br>
例如setfacl -m u:frodo:rw- /file  修改 用户 frodo的权限为 rw- 针对/file文件。<br>

-rw-rw----+    /file  最后是个+号，代表有扩展属性。<br>
使用 getfacl /file   查看权限<br>



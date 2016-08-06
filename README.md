# LearnCentOS
这个项目是我学习CentOS的一个记录

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
ctrl-w ,s 分窗口<br>
set nu 增加行号  <br>
set nonu  取消行号<br>
set ai  自动缩进<br>
可以编辑~目录下的.vimrc<br>
   set number<br>
%s/X86_64/i386/g      全文搜索且替换。go<br>
   
   

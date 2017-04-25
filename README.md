# linux
what are you doing
POST --> Boot Sequeue(BIOS) --> Bootloader(MBR) --> kernel(ramdisk) --> rootfs --> /sbin/init
启动流程 post

Linux文件名的命名要求：
区分大小写、可使用除/以外的任意字符、文件名不能超过255个字符，以.开头的文件是隐藏文件；
家目录，工作目录；
获取命令帮助；
help
man，--help，info
Linux文件系统的基础命令：
常用命令
pwd命令：printing working directory
显示工作目录
~]# echo $PWD
~]# echo $OLDPWD
cd命令：change directory
cd [/PATH/TO/SONMEDIR]
cd：切换回家目录；
ls命令：list，列出指定目录下的内容；
ls [OPTION]... [FILE]...
-a，--all：显示所有文件，包括.和..在内所有隐藏的文件；
-A，--almost-all：显示所以文件，不包括.和..在内的
-l：use a long listing format使用长格式，显示属性信息；
drwxr-xr-x. 2 root root 69 3月 2 01:45 scripts
drwxr-xr-x：分为四段；
d：文件类型，一个字符；
-：表示普通文件；
rwxr-xr-x：文件权限，permission；
perm：
r：readable，可读；
w：writable，可写；
x：excutable，可执行；
权限三位一组：
左三位rwx：属主的访问权限；
中三位r-x：属组的所有用户的访问权限；
右三位r-x：其它（other）用户的访问权限；
-h，--human-readable：对数值做单位换算；
-d：仅查看目录自身属性；
-R：recursive，递归显示；
-r：reverse，降序（逆序）显示；
-i：显示文件的inode号码；
--color={never|auto|always}：何时着色显示；
cat [OPTION]... [FILE]...
-n，--number：对显示出的行进行编号；（与文件没关系）
echo命令：回显
echo [SHORT-OPTION]... [STRING]...
-n：不自动附加换行符；即都在一行显示；
-e：启用转义符，使能转义符\；
\n：换行；
\b：退格；
\t：水平制表符；
\v：垂直制表符；
bash是弱类型的编程语言，不严格区分数据类型，意味着把所有数据统统当做字符串处理；
字符串类型的数据可不加引号；
date命令：系统时间
date [OPTION]... [+FORMAT]：显示日期时间；
date [MMDDhhmm[[CC]YY][.ss]]：设定日期时间；
FORMAT：格式说明
%F：日期，显示为数字，格式为：2016-03-02；
%D：显示英制格式，月日年，显示格式为：03/02/16；
%T：时间，显示为数字，格式为：15:52:16；
%Y：年份，只显示完整年份数字（4位数字），显示格式为：2016；
%y：显示年份的后两位，显示格式为：16；
%m：月份，只显示数字，显示格式为：03；
%d：日期，只显示数字，显示格式为：02；
%H：小时，只显示数字，显示格式为（00..23）：15；
%k：小时，显示格式为（0..23）；
%I：小时，格式为（01..12）；
%l：小时，显示格式为（1..12）；
hwclock命令：硬件时钟
-s, --hctosys：以硬件时间为准；设定系统时间；
-w, --systohc：以系统时间为准；设定硬件时间；
Linux系统上的文件类型：
-：常规文件，有时使用 f 标识；
d：目录文件；
b：block；块设备；
c：character devices；字符设备；
l：sysbolic link files；符号链接文件；
p：pipe，命名管道（可创建管道）；
s：socket，套接字文件；
bash的特性之一：命令别名
获取当前用户可用的别名的定义：
~]# alias
定义别名：
~]# alias NAME='COMMADN'
生命周期：当前shell进程有效；
撤销别名：
~]# unalias NAME
bash特性之三：快捷键
Ctrl+a：跳至命令行首；
Ctrl+e：跳至命令行尾；
shutdown命令：
shutdown [OPTIONS...] [TIME] [WALL...]
选项：
-h：关机；
-r，--reboot：重启；
-P，--poweroff：断电关机；
-k：假操作；
-c：取消尚未执行的关机或重启操作；
TIME：设置将来某时间执行的关机操作；
(1)HH:MM
(2)+m：从此刻开始计算以后的时间；
系统关机或重启命令：
关机：halt，poweroff，init 0，systemctl poweroff，systemctl halt
重启：reboot，init 6，systemctl reboot
which命令：
显示命令完整路径存放位置；
whereis命令：
显示命令的二进制程序、源码和手册文件存放位置；
who命令：
显示登录当前系统的用户
who [OPTION]... [ FILE | ARG1 ARG2 ]
-a：显示详细信息，相当于-b -d --login -p -r -t -T -u同时用的效果；
-r；仅显示运行级别；
-b：仅显示系统本次的启动时间；
w命令：
显示登录的用户及正在执行的命令
whoami命令：
显示当前有效的用户ID（su命令切换用户时可用）；
例如：
~]# chmod ug=rw,o= /tmp/test/fstab：更改文件权限，赋权表示法；
~]# chmod og=r /tmp/test/fstab
例如：
~]# chmod u+x /tmp/test/fstab：更改文件权限，授权表示法;
~]# chmod g+w /tmp/test/fstab
~]# chmod o-r /tmp/test/fstab
~]# chmod ug-x /tmp/test/fstab
chown命令：仅管理员有权限，即能改文件的属主又能改属组，也可同时改；
例如：
~]# chown gentoo /tmp/test/fstab：仅改文件的属主；
~]# chown :mageedu /tmp/test/fstab：仅改文件的属组；
~]# chown gentoo:mageedu /tmp/test/fstab
~]# chown -R --reference=/home/fedora /tmp/fstab
umask：文件的遮罩码；
文件默认权限机制是由umask决定的；
文件权限：
666-umask
目录权限：
777-umask
例如：
~]# ! id hive && useradd hive：如果用户不存在，则添加用户
如何写shell脚本：
脚本文本的第一行：顶格：给出shebang，解释器程序文件的路径，用于指明解释运行当前代码的解释器；
shell脚本是什么：
就是命令的堆积；
但是很多命令不具有幂等性（多次执行产生相同结果即幂等性），需要用程序逻辑来判断运行条件是否满足，以避免运行中
产生错误；
运行脚本：
（1）赋予执行权限，并直接运行此程序文件；
chmod +x /PATH/TO/SCRIPT_FILE
/PATH/TO/SCRIPT_FILE
也可直接把脚本的目录文件放在PATH环境变量中；例如把脚本的目录文件放在/bin目录下；
（2）直接运行解释器，以脚本文件为参数；
bash /PATH/TO/SCRIPT_FILE
~]# nano first.sh
#!/bin/bash
#create user
#
user=storm
! id $user &> /dev/null && useradd $user && echo "user $user add ok" ||echo "user $user exist"
~]# chmod +x first.sh
~]# ./first.sh
配置文件的作用：
（1）profile类：主要为登录式shell初始化环境的；
（2）bashrc类：
用于定义本地变量；
本地变量定义在配置文件中就永久有效；
全局：对所有用户生效；仅管理员有权修改；
/etc/profile（主文件）, /etc/profile.d/*.sh（主文件被切分为多个片段）
/etc/bashrc
用户个人：仅对单个用户生效；
~/.bash_profile
~/.bashrc

shell进程的启动方式有两类：
用户以登录方式启动（登录式shell）：说白了就是启动了一个新bash；
通过终端（使用账户，密码）登录用户启动的shell进程；
使用tty1-6、ssh或telnet远程登录均为登录式shell；
使用su - username或su -l username实现的用户切换也是登录式shell；

可编辑定义登录shell时显示的信息；
例如：在全局中永久生效，应编辑/etc/profile.d/的配置文件；
~]# nano /etc/profile.d/welcome.sh
echo "hello $USER ,welcome to MageEdu,$(date +%F' '%T)"
~]# exec bash：重新执行bash，让配置文件立即生效；
例如：在个人用户中永久生效，应编辑~/.bash_profile的配置文件；
~]# nano /root/.bash_profile
echo "hello $USER ,welcome to MageEdu,$(date +%F' '%T)"








Linux上文本处理三剑客（都支持正则式）
grep，egrep，fgrep：主要用于实现文本搜索工具；基于pattern模式，对给定文本进行搜索操作；
sed：Stream DEitor流编辑器，适用于在脚本中使用的流编辑器，行编辑器；文本编辑工具；
awk：GNU awk，文本格式工具；主要是文本报告生成器；

GREP

常用选项：
--color=auto：对匹配到的文本着色高亮显示；
-i：忽略字符大小写；
-o：仅显示匹配到的文本自身；（默认显示匹配到的文本整行）
-v，--invert-match：反向匹配；

例如：
~]# grep 'root' /etc/passwd：如果模式里有变量要用双引号；
~]# grep -v 'root' /etc/passwd：反向匹配；
~]# grep -i 'root' /etc/passwd：忽略字符大小写；
~]# grep -o 'root' /etc/passwd：仅显示匹配到的文本自身；
~]# grep -q 'root' /etc/passwd：静默模式；
~]# echo $?；取命令执行状态码时常用；

例如：
~]# grep 'root' /etc/passwd：如果模式里有变量要用双引号；
~]# grep -v 'root' /etc/passwd：反向匹配；
~]# grep -i 'root' /etc/passwd：忽略字符大小写；
~]# grep -o 'root' /etc/passwd：仅显示匹配到的文本自身；
~]# grep -q 'root' /etc/passwd：静默模式；
~]# echo $?；取命令执行状态码时常用；
[:alpha:]：任意单个字母；
[:alnum:]：任意单个字母和数字
[:space:]：任意单个空白字符；
[:blank:]：任意单个空格和tab；
[:punct:]：任意单个标点符号；

2、次数匹配：

*：匹配前面的字符出现的任意次（0,1或多次）；
.*：匹配任意长度的任意字符，相当于glob中的*；
\+：匹配前面的字符至少1次（1次或多次）；\为转义符；
\?：匹配前面的字符0次或1次，即前面的字符可有可无；
\{m\}：匹配其前面的字符出现m次，m为非负整数；
\{m,n\}：匹配其前面的字符出现m次，m为非负整数；闭区间[m,n]
\{0,n\}：至多n次；
\{m,\}：至少m次；
3、位置锚定：
限制使用模式搜索文本，限制模式所匹配到的文本只能出现于目标文本的哪个位置；
^：行首锚定；用于模式的最左侧，^PATTERN；
$：行尾锚定；用于模式的最右侧，PATTERN$；
^PATTERN$：要让PATTERN完全匹配一整行；
^$：匹配空行；
^[[:space:]].*$：匹配空白行；
例如：
~]# grep "^r..t" /etc/passwd：匹配r开头后跟两个字符再跟t的行；
~]# grep "l.\{3\}n" /etc/passwd：匹配l后跟3个字符再跟n的行；
~]# grep "l.\{3\}n$" /etc/passwd：匹配l后跟3个字符再跟n结尾的行；
~]# grep "^l.\{3\}n$" /etc/passwd：匹配只能是l开头后跟3个字符再跟n结尾的行；
~]# grep "[[:space:]]\+" /etc/passwd：匹配至少连续出现一个空格的行；
\<或\b：词首锚定，用于单词模式的左侧，格式为\<PATTERN,/bPATTERN；
\>或\b：词尾锚定，用于的承诺模式的右侧，格式为PATTERN\>,PATTERN\b；

练习：
1、显示/etc/passwd文件中不以bash结尾的行；
~]# grep -v 'bash$' /etc/passwd
2、找出/etc/passwd文件中的三位或四位数；
~]# grep '\<[0-9]\{3,4\}\>' /etc/passwd
3、找出/etc/grub2.cfg文件中，以至少一个空白字符开头，后面又跟了一非空白字符的行；
~]# grep '^[[:space:]]\+[^[:space:]]' /etc/grub2.cfg
4、找出"netstat -tan"命令的结果中，以‘LISTEN’后跟0或多个空白字符结尾的行；
~]# netstat -tan | grep 'LISTEN[[:space:]]*$'
5、找出“fdisk -l”命令结果中，以/dev/后跟sd或hd及一个小写字母的行；
~]# fdisk -l | grep '/dev/[sh]d[a-z]\>'
6、找出“ldd /usr/bin/cat”命令的结果中的文件路径；
~]# ldd /usr/bin/cat | grep -o '/[^[:space:]]\+'

4、分组与引用：
\(PATTERN\)：将此PATTERN匹配到的字符当作一个不可分割的整体进行处理；
注意：分组括号中的模式匹配到的字符会被正则表达式引擎自动记录于内部变量中，这些变量是\1,\2,\3,...

egrep：
支持使用扩展的正则表达式的grep命令，相当于grep -E；
egrep [OPTIONS] PATTERN [FILE...]
选项同grep；
扩展正则表达式的元字符：无需转义符；
字符匹配：
.：匹配任意单个字符；
[]：匹配范围内的任意单个字符；
[^]：匹配范围外的单个字符；
[:digit:]：任意单个数字；
[:lower:]：任意单个小写字母：

[:upper:]：任意单个大写字符；
[:alpha:]：任意单个字母；
[:alnum:]：任意单个字母和数字
[:space:]：任意单个空格；
[:blank:]：任意单个空格和tab
[:punct:]：任意单个标点符号；
次数匹配：
*：匹配前面的字符（可有可无）出现的任意次（0,1或多次）；
?：匹配前面的字符0次或1次，即前面的字符可有可无；
+：匹配前面的字符至少1次（1次或多次）；
{m}：匹配其前面的字符出现m次，m为非负整数；
{m,n}：匹配其前面的字符出现m次，m为非负整数；[m,n]
{0,n}：至多n次；
{m,}：至少m次；
位置锚定：
^：行首锚定；用于模式的最左侧，^PATTERN；
$：行尾锚定；用于模式的最右侧，PATTERN$；
^PATTERN$：要让PATTERN完全匹配一整行；
^$：匹配空行
\<,\b：词首锚定，用于单词模式的左侧，格式为\<PATTERN,/bPATTERN；
\>,\b：词尾锚定，用于的承诺模式的右侧，格式为PATTERN\>,PATTERN\b；
分组及引用：
(pattern)：分组，括号中的模式匹配到的字符会被存储于正则表达式引擎内部的变量中；
后向引用：\1,\2,\3,...
或者：
a|b：a或者b
C|cat：表示C或cat；
(C|c)at：表示Cat或cat；
练习：
1、显示/etc/passwd文件中不以bash结尾的行；
~]# egrep -v 'bash$' /etc/passwd
2、找出/etc/passwd文件中的三位或四位数；
~]# egrep '\<[0-9]{3,4}\>' /etc/passwd
3、找出/etc/grub2.cfg文件中，以至少一个空白字符开头，后面又跟了一非空白字符的行；
~]# egrep '^[[:space:]]+[^[:space:]]' /etc/grub2.cfg
4、找出"netstat -tan"命令的结果中，以‘LISTEN’后跟0或多个空白字符结尾的行；
~]# netstat -tan | egrep 'LISTEN[[:space:]]*$'
5、找出“fdisk -l”命令结果中，以/dev/后跟sd或hd及一个小写字母的行；
~]# fdisk -l | egrep '/dev/[sh]d[a-z]\>'
~]# fdisk -l | egrep '/dev/(s|h)d[a-z]\>'
6、找出“ldd /usr/bin/cat”命令的结果中的文件路径；
~]# ldd /usr/bin/cat | egrep -o '/[^[:space:]]+'
7、找出/proc/meninfo文件中，所有以大写或小写s开头的行，至少用三种方式实现；
~]# egrep "^(s|S)" /proc/meminfo
~]# grep "^[sS]" /proc/meminfo
~]# grep -i "^s" /proc/meminfo
8、显示当前系统上root，centos，或slackware用户的相关信息；
~]# egrep "^(root|centos|slackware)\>" /etc/passwd
~]# egrep "^(root|centos|slackware):" /etc/passwd
9、echo输出一个绝对路径，使用grep取出基名；
~]# echo /etc/passwd/ | egrep -o "[^/]+/?$"
10、找出ifconfig命令结果中的1-255之间的整数；
~]# ifconfig| egrep "\<([1-9]|[1-9][0-9]|1[0-9][0-9]|2[0-4][0-9]|25[0-5])\>"




sed内部不仅有模式空间，还有一个空间叫hold space保持空间，可以将被sed模式匹配到的行编辑完以后存放到保持空间里
（高级用法）；
sed [OPTION]... 'script' [input-file]...
script：
地址定界编辑命令
常用选项：
-n：不输出模式空间中的内容至屏幕；
-e script, --expression=script：实现多点编辑；
例如：
]# sed -e 's@^#[[:space:]]*@@' -e '/^UUID/d' /etc/fstab
-f /PATH/TO/SED_SCRIPT_FILE：每行一个sed编辑命令，保存一个文件，读取文件来进行编辑操作；
-r, --regexp-extended：支持使用扩展正则表达式；
-i[SUFFIX], --in-place[=SUFFIX]：直接编辑原文件；
地址定界：（类似vim中末行操作）
（1）不给地址：表示对全文进行处理；
（2）单地址：
#：指定第#行
/pattern/：被此模式所匹配到的每一行；
（3）地址范围
#，#：从第#行开始到第#行结束；
#，+#：从第#行开始，加#行；
#，/pat1/：从第#行开始，到第一次被模式匹配的行结束；
/pat1/,/pat2/：从被模式1匹配到的第一行开始，到被模式2匹配到的第一行结束；
$：最后一行；
（4）不进：~
1~2：表示从1开始，步进2行，如3,5,7行即所有奇数行；
2~2：表示所有偶数行；
sed常用编辑命令：
d：删除模式空间内容；
例如：
]# sed '1,5d' /etc/fstab：删除第1到5行；
]# sed -n '1,5d' ]# /etc/fstab：删除第1到5行，同时不显示模式空间中没被匹配的行；
]# sed '3d' /etc/fstab：删除第3行；
]# sed '/^UUID/d' /etc/fstab：删除以UUID开头的行；
]# sed '1~2d' /etc/fstab：显示偶数行，即删除奇数行；
p：显示模式空间中内容；（根据地址定界和编辑命令后显示）
例如：
]# sed '1~2p' /etc/fstab：显示2遍所有奇数行，即偶数行没被匹配显示一遍，又显示一遍匹配到的奇数行；
]# sed -n '1~2p' /etc/fstab：显示一遍所有奇数行，即不显示没被匹配的行；
]# sed '1~2d' /etc/fstab：显示偶数行，即删除奇数行；
a \test：在匹配到的行后面追加文本"test"，支持使用\n实现多行追加；
i \test：在匹配到的行前面插入文本"test"，支持使用\n实现多行插入；
例如：
]# sed '3i \new line' /etc/fstab：在第三行上面插入一行new line；
]# sed '3a \new line' /etc/fstab：在第三行下面插入一行new line；
]# sed '3a \new line\nanother new line' /etc/fstab：在第三行下面插入2行；
]# sed '/^UUID/a \# add new device base on UUID' /etc/fstab：在UUID开头的行下面添加一行# add new
device base on UUID；
c \test：把匹配到的行替换为此处指定的文本"tes

例如：
]# sed '/^UUID/c \# add new device base on UUID' /etc/fstab：把UUID开头的行替换为# add new device base
on UUID；
w /PATH/TO/SOMEFILE：保存模式空间中匹配到的行至指定的文件中；
例如：
]# sed -n '/^[^#]/p' /etc/fstab：显示非#开头的行；
]# sed -n '/^[^#]/w /tmp/fstab.bak' /etc/fstab：把非#开头的行保存至/tmp/fstab.bak文件里；
]# cat /tmp/fstab.bak：验证保存结果；
r /PATH/TO/SOMEFILE：读取指定文件的内容至当前文件被模式匹配到的行后面，实现文件合并；
例如：
]# sed '3r /etc/issue' /etc/fstab：把issue文件，写在fstab文件第3行的后面（文件合并）；
]# sed '/^UUID/r /etc/issue' /etc/fstab：把issue文件，写在fstab文件中以UUID开头的行后面；
=：为模式匹配到的行打印行号；
例如：
]# sed '/^UUID/=' /etc/fstab：把UUID开头的行上面加一行号；
!：条件取反；
地址定界!编辑命令；
例如：
]# sed '/^[^#]/d' /etc/fstab：删除非#开头的行；
]# sed '/^#/!d' /etc/fstab：删除非#开头的行；
]# ! sed '/^#/d' /etc/fstab：删除非#开头的行；
s///：查找替换，其分隔符可自行指定，常用有s@@@、s###等；
替换标记：
g：全局替换；
w /PATH/TO/SOMEFILE：将替换成功的结果保存至指定文件中；
p：仅显示替换成功的行；

例如：
]# sed '$!N;$!D' /etc/fstab
读第一行，执行不是最后一行执行N读取匹配到的行的下一行并追加至模式空间中（模式空间为第1、2行），执行不
是最后一行，执行D删除多行模式空间中的所有行（模式空间为空）；
读第三行，执行不是最后一行执行N（模式空间有第3、4行），执行不是最后一行执行D（模式空间为空）；
读取倒数第2行时，执行不是最后一行执行N（模式空间有最后2行），执行不是最后一行执行D（此时最后一行已经读
取完了，即不执行D）；结果模式空间中仅保存了最后两行；
sed '/^$/d;G' FILE：删除原有的所有空白行，然后为所有非空白行后添加一个空白行；
例如：
]# sed '/^$/d;G' /etc/fstab
读取第一行，执行是空白行就是执行d删除，执行G把保持空间的内容追加至中模块空间中（统一添加空白行至非空白
行后面）；
sed 'n;d' FILE：显示奇数行；
例如：
]# sed 'n;d' /etc/fstab
读取第一行，执行n读取匹配到的行的下一行覆盖至模式空间中（即用第2行覆盖模式空间中第1行），执行d删除模式
空间中的行；默认显示不匹配到的行，结果显示的都是奇数行；
sed 'G' FILE：在原有的每一行后面添加一个空白行；
例如：
]# sed 'G' /etc/issue
]# sed -i '/^UUID/d' fstab：原处修改；
注意：任何要修改配置文件的操作，事前要先做好备份；





文本查看及处理工具：wc，cut，sort，uniq，diff，patch
wc：单词统计；
wc [OPTION]... [FILE]...
-l：仅显示行数；
-c：仅显示字节数；
-m：仅显示字符数；
-w：仅显示单词数；
cut命令：移除文本行中的字段；
cut OPTION... [FILE]...
-d, --delimiter 'CHAR'：以指定的字符为输入分隔符，默认为空白字符；
-f, --fields FILEDS：挑选出的字段；
#：指定的单个字符
#，#：离散的多个字段，例如1,3,7；
#-#：连续的多个字段，例如，4-7；
当使用空白字符为分隔符，空白符连续多个时，不能正确取出；要使用awk命令；
awk命令简单用法：
awk -F CHAR '/pattern/{print $1,$2,...$NF}' FILE...
-F：指明输入分隔符；
$1,$2：指明字段
$NF：表示最后一个字段，NF表示一行的字段总数；
//：/之间是pattern，支持正则表达式；
sort命令：基于对文本文件的每行首字母在ACII码表中的大小做排序，默认升序排序；
sort [OPTION]... [FILE]...
-r，--reverse：逆序排序；
-u, --unique：相同的行仅显示一次；连续且完全一样为相同；
-t：指定分隔符；
-k #：用在排序的字段；
-n, --numeric-sort：以数值大小排序；
-f，--ignore-case：比较时忽略字符大小写；
uniq命令：同sort -u，通常用管道与sort排序后连用；
uniq [OPTION]... [INPUT [OUTPUT]]
选项：
-d, --repeated：仅显示重复的行；
-u, --unique：仅显示不重复的行；
-c, --count：在每行行首显示其出现的次数；

ping命令：
send ICMP ECHO_REQUEST to network hosts
ping [OPTION] destination
-c #：发送ping包的个数；
-I INTERFACE：指明从哪个接口发送ping命令；
-l：预加载的数据量；
-w #：限定ping命令超时时长；
-W #：一次ping操作中，等待对方响应的超时时长；
-s #：指明ping包报文大小（默认64字节）；

hping3 选项
--fast：快速发送ping包，一秒钟发送10个包，同-i u1000；
--fsater：比--fast更快，尽可能的快速发送ping包；
--flood：洪水发送ping包；
-i u#：发送ping包时间间隔；单位是微秒；
例如：
]# hping --fast 192.168.255.104：快速ping192.168.255.104主机；可以当压力测试使用；


bash脚本编程之算术运算：
算术运算符：
+，-
*，/
%：取余；
**：次方；
算术运算格式：
（1）let VAR=算术表达式；放在VAR变量中以便引用；
例如：let a=$num1+$num2；
（2）VAR=$[算术表达式]；可单独使用，不用赋值变量；
例如：c=$[$num1+$num2]
或：echo $[$num1+$num2]
（3）VAR=$((算术表达式))
例如：echo $(($num1+$num2))
（4）VAR=$(expr $ARG1 $OP $ARG2)：乘法*需要转义；
命令引用赋值给变量，方便以后引用；
注意：乘法符号*在有些情况下需要转义；

语法
let VAR=expression
VAR= $[expression]
VAR= $((expression))
VAR=$(expr argu1 argu2 argu3)
VAR=`expr argu1 OP argu2`
注意：有些时候乘法符号需要转义；

增强型变量赋值：
例如：
declare -i i=1 此时就可用增强型赋值：
i=$[$i+1] let i+=1
echo $i
变量做某种算术运算后回存至此变量中；
let i=$i+#
let i+=#
#：代表数字
+=，-=，*=，/=，%=在shell脚本中要使用let

自增：
VAR=$[$VAR+1]
let VAR+=1
let VAR++
自减：
VAR=$[$VAR-1]
let VAR-=1
let VAR--

bash的测试类型：
数值测试
字符串测试
文件测试
数值测试：数值之间的比较
-eq：是否等于；例如：[ $num1 -eq $num2 ]，test 2 -eq 3或[ 2 -eq 3 ]
-ne：是否不等于；
-gt：是否大于；
-ge：是否大于等于；
-lt：是否小于；
-le：是否小于等于；
例如：
]# test 2 -gt 3
]# [ $A -eq $B ]

字符串测试比较
==：是否等于，等于为真；
!=：是否不等，不等于为真；
>：是否大于，大于为真；
<：是否小于，小于为真；
=~：左侧字符串是否能被右侧的PATTERN所匹配（左边是否包含右边），包含为真；
注意：变量赋值为用字符串时要有引号，即使的空字符也要用引号，以防出错，因为shell脚本一旦遇到错误，立即退出，字符
判断使用双中括号[[]]。
例如：
]# name=uubuntuu
]# [[ "$naem" =~ buntu ]]
]# echo $?
练习：
判断主机名是否包含magedu，如果不包含，则修改为magedu；
]# a=$(hostname)
]# [[ "$name" =~ magedu ]] || hostname magedu

-z "STRING"：判断指定的字符串是否为空；
-n "STRING"：判断指定的字符串是否不空；
不空则为真，空则为假；
注意：
（1）字符串比较要加引号，表示引用；即不做变量替换可用单引号，做变量替换要用双引号；
（2）字符串比较时，要使用[[ ]]双中括号；
文件测试：
存在性测试
-a FILE
-e FILE：文件的存在性测试，如果存在，则为真；
例如：
]# [ -e /etc/passwd ]

文件的存在性及文件类型测试：既能测试存在性又能测试类别
-b FILE：文件是否存在并且为块设备文件；
-c FILE：文件是否存在并且为字符设备文件；
-d FILE：文件是否存在并且为目录文件；
-f FILE：文件是否存在并且为普通文件；
-h FILE或-L FILE：文件是否存在并且为符号链接文件；
-p FILE：文件是否存在并且为命名管道文件；
-S FILE：文件是否存在并且为套接字文件；
例如：
]# [ -c /dev/null ]
文件权限测试：
-r FILE：文件是否存在并且对当前用户可读；
-w FILE：文件是否存在并且对当前用户可写；
-x FILE：文件是否存在并且对当前用户可执行；
例如：
[ -w /etc/passwd ] && echo ok
特殊权限测试：
-u FILE：文件是否存在并且拥有SUID权限；
-g FILE：文件是否存在并且拥有SGID权限；
-k FILE：文件是否存在并且拥有sticky权限；

脚本的状态返回值：
默认是脚本中执行的最后一条命令的状态返回值；
自定义状态退出状态码；
exit [n]：n为自己指定的状态码；
注意：shell进程遇到exit时，即会终止，因此，整个脚本执行即为结束；
所以，exit不能随意添加使用，要使用条件测试判断后，确定是否添加exit退出；
埋点调试；使用$?能判断是在哪个位置退出的，定位问题常用；

练习：
脚本实现，通过命令传递两个文本路径给脚本，计算其空白行数（^$）之和；
a=$(egrep "^$" $1|wc -l)
b=$(egrep "^$" $2|wc -l)
sum=$[$a+$b]
echo "a is :$a"
echo "b is $b"
echo "sum is :$sum"

练习：
1、判断/etc/passwd是否为文件，如果为文件，则输出/etc/passwd is files，该路径通过命令传递的方式传入，当传入
的命令个数大于1，则报错；
[ $# -gt 1 ] && echo "something wrong " && exit 100
[ -f $1 ] && echo "/etc/passwd is files"
2、在root目录下，写脚本，可以一次性添加3名用户，通过传递参数的方式，进行用户添加，当传递的参数不符合3个的
时候，报错；
当三名用户添加完成后，需要将脚本进行权限加固(锁机制，不能再执行)，将脚本权限改成属主可读可写可执行；
! [ $# -eq 3 ] && echo "please give me three username" && exit 1
useradd $1 && a=1
useradd $2 && b=1
useradd $3 && c=1
sum=$[$a+$b+$c]
[ $sum -eq 3 ] && echo "$1 $2 $3" ||exit 2
chmod 700 $0
echo $1 is added
echo $2 is added
echo $3 is added
echo "this scripts mode is 700"


条件判断（选择分支）：
shell执行是顺序执行的
选择分支
单分支的if语句
if 测试条件；then（如果条件为真，则执行下面语句）
代码分支
fi
或
if 测试条件
then
代码分支
fi
双分支的if语句
if 测试条件；then
条件为真时执行的分支
else
条件为假时执行的分支
fi
多分支的if语句
if 测试条件；then
条件为真时候执行的分支
elif 测试条件；then
elif 测试条件；then
elif 测试条件；then
else
条件为假时候执行的分支
fi
例如：
通过参数传递给一个用户名给脚本，此用户如果不存在则创建用户；
if ! grep "^$1\>" /etc/passwd &> /dev/null;then
useradd $1
echo $1|passwd --stdin $1 &> /dev/null
echo "add a user $1 finished"
else
echo "$1 is exist"
fi

练习：
1、通过命令参数，给定两个数字，输出其中较大的数值；
if [ $1 -gt $2 ] ;then
echo $1 is bigger
else
echo $2 is bigger
fi
或：
if [ ! $# -eq 2 ];then
echo "give two number"
exit 2;
fi
if [ $1 -gt $2 ];then
echo "the bigg is $1"
elif [ $1 -lt $2 ];then
echo "the bigg is $2"
else
echo "$1=$2"
fi
2、通过命令参数，给定两个文本文件名，如果某文件不存在，则结束脚本，如果都存在返回每个文件的行数，并echo其
中行数较多的文件名；
[ $# -ne 2 ] && echo "give two file" && exit 1
if ! [ -e $1 ];then
echo "$1 is not find"
exit 2
elif ! [ -e $2 ];then
echo "$2 is not find"
exit 3
fi
f1=$(cat $1|wc -l)
f2=$(cat $2|wc -l)
echo "$1 line is $f1"
echo "$2 line is $f2"
if [ $f1 -gt $f2 ];then
ehco "$f1 is more"
elif [ $f1 -eq $f2 ];then
echo "f1 and f2 the same"
else
echo "$f2 is more"
fi
或：
if ! [ $# -eq 2 ];then
echo "give 2 files"

用户交互：通过键盘输入数据
read [OPTION] ... [name ...]
-p 'PROMPT'：输出提示符，设置提示信息；；
-t TIMEOUT：设定超时退出时间；
name：是在脚本里设定的变量；
bash -n /path/to/some_script
检测脚本中的语法错误
bash -x /path/to/some_script
调试执行
例如：脚本实现，使用read添加用户，密码同用户名；
read -p "plase give a username and passwd: " a b
useradd $a
echo $a
echo $b
echo "$b "| passwd $a --stdin &> /dev/null

bash脚本编程
顺序执行
选择执行：if，case
循环执行：for，while，until
for循环格式：
for VARAIBLE in LIST;do
循环体
done
LIST列表生成方式有多种：直接给出，{#..#}，或glob（/tpm/test/*）等任何能够返回列表的命令都可以；
while循环：
while CONDITION;do
循环体
循环扩展变量修正表达式（条件修正表达式）
done
进入条件：CONDITION参数为“真”；
退出条件：CONDITION参数为“假”；
until循环：
until CONDITION;do
循环体
循环扩展变量修正表达式（条件修正表达式）
done
进入条件：CONDITION参数为“假”；
退出条件：CONDITION参数为“真”；
until就相当于在while条件前取反（!）的效果；
例如：求100内正整数和；
比for优势在于，如果数值比较多，for的列表会占用内存，while则使用的是变量，占用内存空间很小；
for循环：
for i in {1..100};do
sum=$[$sum+$i]
done
echo $sum
while循环：
declare -i sum=0
declare -i i=1
while [ $i -le 10 ];do
sum=$[$sum+$i]
let i++
done
echo $sum
until循环：
declare -i sum=0
declare -i i=1
until [ $i -gt 100 ];do
let sum+=$i
let i++
done
echo $sum
练习：分别使用for、while、until各自实现；

1、求100内所有偶数之和、奇数之和；
while循环100内奇数、偶数和
declare -i i=1
declare -i evensum=0
declare -i oddsum=0
while [ $i -lt 101 ];do
if [ $[$i%2] -eq 0 ];then
let evensum+=$i
else
let oddsum+=$i
fi
let i++
done
echo "使用while循环计算100内偶数、奇数和"
echo "偶数和为：$evensum"
echo "奇数和为：$oddsum"
echo "sum=$[$evensum+$oddsum]"
for循环实现100内奇数、偶数和
for ((i=0;i<=100;i++));do
if [ $[$i%2] -eq 0 ];then
let evensum+=$i
else
let oddsum+=$i
fi
done
echo "使用for循环计算100内偶数、奇数和"
echo "偶数和为：$evensum"
echo "奇数和为：$oddsum"
echo "sum=$[$evensum+$oddsum]"
until循环实现100内奇数、偶数和
until [ $i -gt 100 ];do
if [ $[$i%2] -eq 0 ];then
let evensum+=$i
else
let oddsum+=$i
fi
let i++
done
echo "使用until循环计算100内偶数、奇数和"
echo "偶数和为：$evensum"
echo "奇数和为：$oddsum"
echo "sum=$[$evensum+$oddsum]"
2、创建10个用户，分别为user101-user110；密码同用户名；
for循环创建10个用户，user101-user110，密码同用户名
for i in {101..110};do
name=user$i
id $name &> /dev/null
if [ $? -eq 0 ];then
echo "$name用户已存在"
else
useradd $name &> /dev/null
echo "$name"|passwd --stdin $name &> /dev/null
echo "添加用户$name完成"
fi
done
echo "从user101到user110，已经完10个用户"
while循环创建10个用户，user101-user110，密码同用户名
declare -i i=101
while [ $i -lt 111 ] ;do
name=user$i
id $name &> /dev/null
if [ $? -eq 0 ];then
echo "$name用户已存在"
else
useradd $name &> /dev/null
echo "$name"|passwd --stdin $name &> /dev/null
echo "添加用户$name完成"
fi
let i++
done
echo "从user101到user110，已经完10个用户"
until循环创建10个用户，user101-user110，密码同用户名
declare -i i=101
until [ $i -gt 111 ] ;do
name=user$i
id $name &> /dev/null
if [ $? -eq 0 ];then
echo "$name用户已存在"
else
useradd $name &> /dev/null
echo "$name"|passwd --stdin $name &> /dev/null
echo "添加用户$name完成"
fi
let i++
done
echo "从user101到user110，已经完10个用户"
3、打印九九乘法表；
提示：
1x1=1
1x2=2,2x2=4
1x3=3,2x3=6,3x3=9
循环嵌套：
外循环控制乘数，内循环控制被乘数；
for j in {1..9};do
for i in $(seq 1 $j);do
echo -n -e "${i}x${j}=$[${i}*${j}]\t"
done
echo
done
for循环实现99乘法表
for j in {1..9};do
for i in $(seq 1 $j);do
echo -n -e "${i}x${j}=$[${i}*${j}]\t"
done
echo
done
for ((j=1;j<=9;j++));do
for ((i=1;i<=j;i++));do
echo -e -n "${i}x${j}=$[${i}*${j}]\t"
done
echo
done
while循环实现99乘法表
declare -i i=1
while [ $i -le 9 ];do
j=1
while [ $j -le $i ];do
echo -e -n "${j}x${i}=$[${j}*${i}]\t"
let j++
done
echo
let i++
done
until循环实现99乘法表
declare -i i=1
until [ $i -gt 9 ];do
j=1
until [ $j -gt $i ];do
echo -e -n "${j}x${i}=$[${j}*${i}]\t"
let j++
done
echo
let i++
done
4、打印逆序九九乘法表；
for逆序99乘法表
for ((j=9;j>0;j--));do
for ((i=1;i<=j;i++));do
for ((i=j;i>0;i--));do
for i in $(seq 1 $j |sort -r);do
for i in $(seq 1 $j);do
echo -e -n "${j}x${i}=$[${j}*${i}]\t"
done
echo
done
while逆序99乘法表
declare -i j=9
while [ $j -gt 0 ];do
i=1
while [ $i -le $j ];do
echo -e -n "${j}x${i}=$[${j}*${i}]\t"
let i++
done
echo
let j--
done
until逆序99乘法表
declare -i j=9
until ! [ $j -gt 0 ];do
i=1
until ! [ $i -le $j ];do
echo -e -n "${j}x${i}=$[${j}*${i}]\t"
let i++
done
echo
let j--
done


循环控制：break，continue
while、for循环的特殊用法
break跳出循环，continue跳出本轮循环，他们也都可以控制n层循环，如果在循环可嵌套中使用break只能跳出break所在层的循
环，使用break 2可再向外跳出层循环；
for(());do
循环体
done
while read VARAIBLE;do
循环体
done < /PATH/FROM/SOMEFILE
bash脚本编程：
顺序执行
条件选择：if（单分支，双分支，多分支），case
循环执行：for，while，until
case语句：
if中的多分支in语句：
if CONDITION1;then
分支1（CONDITION1为真时执行的语句）
elif CONDITION2;then
分支2（CONDITION2为真时执行的语句）
...
else CONDITION;then
分支n
fi
示例：显示菜单给用户，
disk) show disk info
mem) show memory info
cpu) show cpu info
*) QUIT
要求：（1）提示用户给出自己的选择；
（2）正确的选择给出相应信息，否则，提示重新选择正确的选项；
cat << EOF
cpu) display cpu information
mem) display memory infomation
disk) display disks infomation
quit) quit
==============================
EOF
read -p "Enter your choice: " option
while [ "$option" != "cpu" -a "$option" != "mem" -a "$option" != "disk" -a "$option" != "quit" ];do
echo "cpu,mem,disk,quit,please see "
read -p "Enter your choice again: " option
if [ "$option" == "cpu" ];then
lscpu
elif [ "$option" == "mem" ];then
free -m
elif [ "$option" == "disk" ];then
fdisk -l /dev/[hs]d[a-z]
else

下面2语句为服务脚本格式
# chkconfig: - 50 50
# description: test service script
#
prog=$(basename $0)
lockfile=/var/lock/subsys/$prog
case $1 in
start)
if [ -f $lockfile ];then
echo "$prog is running yet"
else
touch $lockfile
[ $? -eq 0 ] && echo "start $prog finished"
fi
;;
stop)
if [ $lockfile ];then
rm -f $lockfile
[ $? -eq 0 ] && echo "stop $prog finished"
else
echo "$prog is not running"
fi
;;
restart)
if [ -f $lockfile ];then
rm -f $lcokfile
touch $lockfile
echo "restart $prog finished"
else
touch -f $lockfile
echo "start $prog finished"
fi
;;
status)
if [ -e $lockfile ];then
echo "$prog is running"
else
echo "$prog is stopped"
fi
;;
*)
echo "Usage :$prog {start|stop|restart|status}"
exit 1
esac

使用函数：
userinfo() {
if id "$username" &> /dev/null;then
grep "^$username\>" /etc/passwd|cut -d: -f3,7
else
echo "no such user"
fi
}
username=$1
userinfo
username=$2
userinfo

练习：
1、脚本函数实现ping主机，来测试主机的在线状态；
主程序：实现测试172.16.1.1-172.16.67.1范围内个主机的在线状态；
分别使用for，while和until循环实现；
普通方式：
declare -i uphosts=0
declare -i downhosts=0
for i in {1..67};do
if ping -W 1 -c 1 172.16.$i.1 &>/dev/null;then
echo "172.16.$i.i is up"
let uphosts+=1
else
echo "172.16.$i.1 is down"
let downhosts+=1
fi
done
echo "Up hosts: $uphosts,Down hosts: $downhosts"
改版2：函数+while循环方式：
declare -i uphosts=0
declare -i downhosts=0
declare -i i=1
hostping() {
if ping -W 1 -c 1 $1 &>/dev/null;then
echo "$i is up"
let uphosts+=1
else
echo "$1 is down"
let downhosts+=1
fi
}
while [ $i -le 67 ];do
hostping 172.16.$i.1
let i++
done
echo "Up hosts: $uphosts,Down hosts: $downhosts"
改版3：使用return，在主程序中统计ping的主机数量；
declare -i uphosts=0
declare -i downhosts=0
declare -i i=1
hostping() {
if ping -W 1 -c 1 $1 &>/dev/null;then
echo "$i is up"
return 0
else
echo "$1 is down"
return 1
fi
}
while [ $i -le 67 ];do
hostping 172.16.$i.1
[ $? -eq 0 ] && let uphosts++ || let downhosts++
let i++
done
echo "Up hosts: $uphosts,Down hosts: $downhosts"

2、脚本函数实现，打印nn乘法表；
变量作用域：
局部变量：作用域是函数的生命周期；在函数结束时被自动销毁；
定义局部变量的方法：local VARIABLE=VALE
本地变量：作用域是运行脚本的shell进程生命周期；因此，其作用范围就是当前shell脚本程序文件；
例如：
name=tom
setname() {
name=jerry
echo "Function: $name"
}
setnaem
echo "Shell: $name"
此时函数的name和shell的name都是jerry，变量name为本地变量，可在函数中调用；
显示结果为：
Function:jerry
Shell: jerry
如果在以上语句中改为：local name=jerry
显示结果为：
Function:jerry
Shell: tom
函数递归：
函数直接或间接调用自身；
做阶乘或斐波那契数列时会用到函数递归；
例如：10！=10*9！=10*9*8！=10*9*8*7！...=10*9*8*7*6*5*4*3*2*1!
函数阶乘 传递参数为n
n*(n-1)!=n*(n-1)*(n-2)!=...
例如：斐波那契数列
每一个数值都是前2个数的和；求第n阶的数是多少就用函数；
1 1 2 3 5 8 13 21 ...
例如：传递参数为一个数字，实现数字的阶乘；
fact() {
if [ $1 -eq 0 -o $1 -eq 1 ];then
echo 1
else
echo $[$1*$(fact $[$1-1])]
fi
}
fact $1
例如：传递参数为一个数字，实现斐波那契数列
fab() {
if [ $1 -eq 1 ];then
echo -n "1 "
elif [ $1 -eq 2 ];then
echo -n "1 "
else
echo -n "$[$(fab $[$1-1])+$(fab $[$1-2])] "
fi
}
for i in $(seq 1 $1);do
fab $i
done
echo
Systemd：（CentOS 7）

声明数组：
declare -a NAME：声明索引数组；
declare -A NAME：声明关联数组；













Section 1: 常用运维awk命令



统计tomcat每秒的带宽(字节)，最大的排在最后面
#cat localhost_access_log.txt | awk '{ bytes[$5] += $NF; }; END{for(time in bytes) print   bytes[time] " " time}'  | sort -n

统计某一秒的带宽
#grep "18:07:34" localhost_access_log.txt |awk '{ bytes += $NF; } END{ print  bytes }'


统计指定ip.txt中ip在local_access.txt中出现的次数
#cat ip.txt //内容如下 
12.3.4.5
12.3.4.6
12.3.4.7
12.3.4.8

#cat local_access.txt
19:23:35  /a.html   12.3.4.5
19:23:35  /b.html   12.3.4.5
19:23:35  /c.html   12.3.4.6
19:23:35  /d.html   12.3.4.7
19:23:35  /a.html   12.3.4.9
19:23:35  /b.html   12.3.4.9
19:23:35  /c.html   12.3.4.9

#awk -F " " '{if (NR==FNR) {arr1[$1]=1} else{arr2[$3]++;}} END{for(ip in arr1){print ip,arr2[ip]}}' ip.txt local_access.txt
12.3.4.5 2
12.3.4.6 1
12.3.4.7 1
12.3.4.8



Section 2: $0,$1,$2,$NF,$(NF-1)的使用



$0整个当前行， $1当前行的第一个域   $NF为最后一个域   $(NF-1)为倒数第二个
#echo "a b c d e" |awk '{print $1; print $2; print $(NF-1);print $NF;print $0}'
a                 //对应第1个域
b                 //对应第2个域
d                 //对应$(NF-1),对应倒数第二个域
e                 //对应$NF,最后一个域
a b c d e         //对应$0


Section 3: print, printf用法


#awk 'BEGIN{a=1;b="213";print "output "a","b;}'
output 1,213


#awk 'BEGIN{a=1;b="213";print "output",a,","b;}'
output 1 ,213

printf的使用
＃awk 'BEGIN{a=1;b="213";printf("output %d,%s\n",a,b)}'
output 1,213


Section 4: 选择分隔符


awk默认是按照空格来分割, NF表示域的个数
#echo "a:b c,d" |awk '{print $1; print $2; print NF}'
a:b
c,d
2


根据":",空格，","来进行分割
#echo "a:b c,d" |awk -F " |,|:" '{print $1; print $2; print NF}'
a
b
4


Section 5: BEGIN,END用法


abc.txt内容如下：
first lady
second boy
third child


#cat abc.txt |awk 'BEGIN {print "begin process"} {print "process 1 "$1} {print "process 2 "$2} END { print " the end"}'
换行后如下:

#cat abc.txt |awk -F " " '
         'BEGIN {print "begin process"}     //在开头的时候执行一次
               {print "process 1 "$1}       //每一行执行一次
               {print "process 2 "$2}       //每一行执行一次
          END  { print " the end"}'         //最后的时候执行一次

输出如下
begin process      
process 1 first         // {print "process 1 "$1}  执行了一次
process 2 lady          // {print "process 2 "$2}  执行了一次
process 1 second
process 2 boy
process 1 third
process 2 child
 the end


没有BEGIN，只有END的情况
#cat abc.txt |awk '{print "begin process"} {print "process 1 "$1} {print "process 2 "$2} END { print " the end"}'
  格式化语句如下
#cat abc.txt |awk -F ":"
  '{print "begin process"}          //因为没有BEGIN  所以这个每一行都会执行
   {print "process 1 "$1}           //每一行都会执行
   {print "process 2 "$2}           //每一行都会执行
    END { print " the end"}'        //最后执行一次
    
输出如下:    
begin process
process 1 first
process 2 lady
begin process
process 1 second
process 2 boy
begin process
process 1 third
process 2 child
 the end


Section 6: 数组使用


awk中数据结构使用, 数组也可以理解为map

#awk 'BEGIN{array1["a"]=1;array1[2]="213";print array1["a"],array1[2]}'
1 213

year.txt中内容如下  

2016:09 1    //表示2016年9月，有一个访问
2016:06 1
2016:06 1
2016:01 1
2015:01 1
2014:01 1
2015:01 1
2016:02 1


下面语句是把每个月的访问量相加,排序后输出
#awk  '{bytes[$1]+=$2}  END { for(time in bytes) print bytes[time],time}' year.txt |sort -n

展开如下
#awk
    '{bytes[$1]+=$2}             //bytes为数组，下标是时间，value是访问量
      END {
          for(time in bytes) print bytes[time], time
      }'
      year.txt |sort -n


输出的内容如下；   bytes是一个数组，下标是字符串""上面用数组，下标可以是数字，也可以是字符串
1 2014:01
1 2016:01
1 2016:02
1 2016:09
2 2015:01
2 2016:06


＃awk 'BEGIN{tB["a"]="a1";tB["b"]="b1";if(tB["c"]!="1"){print "no found";};for(k in tB){print k,tB[k];}}' 

展开是如下
＃awk 'BEGIN{
          tB["a"]="a1";
          tB["b"]="b1";
          if(tB["c"]!="1"){           //这个地方会判断在里面，但是会往tB占用一个值
              print "no found";
          };
          for(k in tB){
              print k,tB[k];
          }
       }' 

输出如下：
no found
a a1
b b1
c                   很奇怪，  “c”没有赋值，循环的时候，就发现在里面了，这个里面有副作用


要修改这个点，需要使用如下
#awk 'BEGIN {
         tB["a"]="a1";
         tB["b"]="b1";
         if ("c" in tB) {                      //用这个来进行判断，就没有负作用
             print "c is in tB";
         } 
         for(k in tB){
             print k,tB[k];
         }
      }'



awk的多维数组


#awk 'BEGIN{ for(i=1;i<=3;i++) {for(j=1;j<=3;j++) {tarr[i,j]=i*j;print i,"*",j,"=",tarr[i,j]}}}'

展开后如下:
＃awk 'BEGIN{
          for(i=1;i<=3;i++) {
              for(j=1;j<=3;j++) {
                  tarr[i,j]=i*j;
                  print i,"*",j,"=",tarr[i,j]
              }
          }
      }'

输出如下：
1 * 1 = 1
1 * 2 = 2
1 * 3 = 3
2 * 1 = 2
2 * 2 = 4
2 * 3 = 6
3 * 1 = 3
3 * 2 = 6
3 * 3 = 9



awk多维数组的in判断

awk 'BEGIN{ tarr[1,3]=5;if ((1,3) in tarr) print "1,3 in"; if ((4,4) in tarr) print "4,4 in"}'

＃awk 'BEGIN{ 
          tarr[1,3]=5;
          if ((1,3) in tarr)          //直接使用(1,3)来判断in语句
              print "1,3 in"; 
          if ((4,4) in tarr) 
              print "4,4 in"}'


Section 7: for语句使用


＃awk 'BEGIN{array1["a"]=1;array1["c"]=3;array1["b"]=2;for(index1 in array1) print index1,array1[index1]}'

展开如下:
#awk 'BEGIN{
          array1["a"]=1;
          array1["c"]=3;
          array1["b"]=2;
          for(index1 in array1)
              print index1,array1[index1]
      }'


输出如下：
a 1
b 2
c 3


for也可以使用k=1;k<=3;k++的形式

#awk 'BEGIN{array1[1]="a";array1[3]="c";array1[2]="b";len=length(array1);for(k=1;k<=len;k++) print k,array1[k]}'

展开如下:
#awk 'BEGIN{
          array1[1]="a";
          array1[3]="c";
          array1[2]="b";
          len=length(array1);        //得到数组的长度
          for(k=1;k<=len;k++) 
              print k,array1[k]
      }'

输出如下
1 a
2 b
3 c


Section 8: 内置函数使用


int函数，把字符串转为整数
#awk 'BEGIN {print int("12.9")}'        返回一个整数
12 


index函数  
#awk 'BEGIN {print index("12.9343",".")}'     //index方法返回"."在"12.9343的位置，没有找到则返回0
3


length函数    得到数组的长度,字符串长度
#awk 'BEGIN{array1["a"]=1;array1["b"]=2;print length(array1)}'
输出如下:
2

#awk 'BEGIN{a="123";print length(a)}'   得到字符串长度
3


match函数，   检测info中是否含有"te" 如果有，则返回"te"第一次出现的位置，如果没有则返回0

#awk 'BEGIN {info="is is test"; print match(info,"te");}'


rand函数   生成随机数   但是事实上是不随机的

#awk 'BEGIN {print rand " " rand}'    rand会生成一个0-1的数字

0.840188 0.394383         //每次运行第一个，第二个都是这个数字


split函数  按照某个分隔符，对字符串进行分割

split按照" "对"it is a test"进行切割，切割后的内容放在thearray中 返回的是split后，thearray的元素个数，

#awk 'BEGIN {print split("it is a test",thearray," "); print thearray[1]}'
4                    //split后返回数组的长度
it                   //打印第一个元素


sub函数   替换
#awk 'BEGIN {info="this a test"; sub("a","b",info); print info }'   把info中"a"用"b"替代

this b test


substr函数   得到子字符串
substr(s, m, n)     s是要截取的字符串,m是开始点，从1开始，   n是要截取的长度

#awk 'BEGIN {print substr("12.9343",2,4)}'      //substr
2.93


toupper函数   字符串转为大写
#awk 'BEGIN {info="this a test"; print toupper(info);}'
THIS A TEST


tolower函数   字符串转为消协
#awk 'BEGIN {info="thIS A TEST"; print tolower(info);}'
this a test


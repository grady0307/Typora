# Linux

## 系统组成

- Linux系统内核
- 系统级应用程序

虚拟机快照

- 保存当前虚拟机的状态，坏了再恢复

## 基础命令

### 目录结构

linux只有一个顶级目录`/`

windows有多个顶级目录，即多个盘符

### 命令入门

![image-20230905110503455](Linux.assets/image-20230905110503455.png)

### ls命令

- `ls [-a -l -h] [linux路径]`
- `-a`列出隐藏文件，`-l`以列表形式列出，`-h`看文件大小，可组合使用

- 作用：列出目录下的内容
- home目录为每个用户的个人账户目录`/home/grady`，默认工作目录的home目录

### cd和pwd

cd  :Change Directory

![image-20230905144732823](Linux.assets/image-20230905144732823.png)

pwd  :Print Work Directory

- 查看当前工作目录

- 无参数，无选项

相对路径和绝对路径

- `cd /home/grady/desktop`
- `cd desktop`

特殊路径符

![image-20230905145219185](Linux.assets/image-20230905145219185.png)

### mkdir

mkidr :Make Directory

- `mkidr [-p] Linux路径`
- 参数必填
- -p可选，表示自动创建不存在的父目录
- ==创建文件夹需要修改权限，涉及到权限问题，HOME外无法成功==

### 文件操作命令

touch

- `touch Linux路径`
- 无选项，参数必填，用于创建文件

cat

- `cat Linux路径`
- 查看内容

more

- `more Linux路径`
- 查看内容，支持翻页
- 查看时空格翻页，q退出

cp

- `cp [-r] 参数1 参数2`
- -r，用于复制文件夹，表示递归
- 参数1：被复制的文件和文件夹
- 参数2：目标地址

mv

- `mv 参数1 参数2`
- 移动文件或文件夹

rm

- `rm [-r -f] 参数1...参数N`
- 用于删除文件或文件夹
- -r用于删除文件夹
- -f表示force，强制删除
- ![image-20230905151540742](Linux.assets/image-20230905151540742.png)

### 查找命令

which

- 查找命令对应的程序文件

find

- `find 起始路径 -name "文件名"`
- 可以使用通配符*进行模糊匹配
- 也可以按文件大小来搜索
- ![image-20230905153927392](Linux.assets/image-20230905153927392.png)

### grep

![image-20230905202331101](Linux.assets/image-20230905202331101.png)

### wc

![image-20230905202731935](Linux.assets/image-20230905202731935.png)

### 管道符

含义：将左边命令的结果，作为右边命令的输入

- `cat test1.txt|grep "of"`
- 可以嵌套使用

### echo tail 重定向符

echo

![image-20230911153655439](Linux.assets/image-20230911153655439.png)

``

- 被``包围的字符会当作命令来执行

重定向符

- ![image-20230911154008827](Linux.assets/image-20230911154008827.png)

tail

- ![image-20230911154459362](Linux.assets/image-20230911154459362.png)

### vi编辑器

![image-20230911175708220](Linux.assets/image-20230911175708220.png)

命令模式常用命令：

- **i** -- 切换到输入模式，在光标当前位置开始输入文本。

- **x** -- 删除当前光标所在处的字符。

- **:** -- 切换到底线命令模式，以在最底一行输入命令。

- **a** -- 进入插入模式，在光标下一个位置开始输入文本。

- **o**：在当前行的下方插入一个新行，并进入插入模式。

- **O** -- 在当前行的上方插入一个新行，并进入插入模式。

- **dd** -- 剪切当前行。

- **yy** -- 复制当前行。

- **p** -- 粘贴剪贴板内容到光标下方。

- **P** -- 粘贴剪贴板内容到光标上方。

- **u** -- 撤销上一次操作。

- **Ctrl + r** -- 重做上一次撤销的操作。

- **:w** -- 保存文件。

- **:q** -- 退出 Vim 编辑器。

- **:q!** -- 强制退出Vim 编辑器，不保存修改。

- 0：这是数字『 0 』：移动到这一行的最前面字符处 (常用)

- [Ctrl] + [f]：屏幕『向下』移动一页，相当于 [Page Down]按键 (常用)

- G：移动到这个档案的最后一行(常用)

- gg：移动到这个档案的第一行，相当于 1G 啊！ (常用)

- | 搜索替换                                           |                                                              |
  | :------------------------------------------------- | ------------------------------------------------------------ |
  | /word                                              | 向光标之下寻找一个名称为 word 的字符串。例如要在档案内搜寻 vbird 这个字符串，就输入 /vbird 即可！ (常用) |
  | ?word                                              | 向光标之上寻找一个字符串名称为 word 的字符串。               |
  | n                                                  | 这个 n 是英文按键。代表重复前一个搜寻的动作。举例来说， 如果刚刚我们执行 /vbird 去向下搜寻 vbird 这个字符串，则按下 n 后，会向下继续搜寻下一个名称为 vbird 的字符串。如果是执行 ?vbird 的话，那么按下 n 则会向上继续搜寻名称为 vbird 的字符串！ |
  | N                                                  | 这个 N 是英文按键。与 n 刚好相反，为『反向』进行前一个搜寻动作。 例如 /vbird 后，按下 N 则表示『向上』搜寻 vbird 。 |
  | :n1,n2s/word1/word2/g                              | n1 与 n2 为数字。在第 n1 与 n2 行之间寻找 word1 这个字符串，并将该字符串取代为 word2 ！举例来说，在 100 到 200 行之间搜寻 vbird 并取代为 VBIRD 则： 『:100,200s/vbird/VBIRD/g』。(常用) |
  | **:1,$s/word1/word2/g** 或 **:%s/word1/word2/g**   | 从第一行到最后一行寻找 word1 字符串，并将该字符串取代为 word2 ！(常用) |
  | **:1,$s/word1/word2/gc** 或 **:%s/word1/word2/gc** | 从第一行到最后一行寻找 word1 字符串，并将该字符串取代为 word2 ！且在取代前显示提示字符给用户确认 (confirm) 是否需要取代！(常用) |
  | .                                                  | 不要怀疑！这就是小数点！意思是重复前一个动作的意思。 如果你想要重复删除、重复贴上等等动作，按下小数点『.』就好了！ (常用) |
  | r, R                                               | 进入取代模式(Replace mode)： r 只会取代光标所在的那一个字符一次；R会一直取代光标所在的文字，直到按下 ESC 为止；(常用) |

  | vim 环境的变更 |                                                    |
  | :------------- | -------------------------------------------------- |
  | :set nu        | 显示行号，设定之后，会在每一行的前缀显示该行的行号 |
  | :set nonu      | 与 set nu 相反，为取消行号！                       |

  特别注意，在 vi/vim 中，数字是很有意义的！数字通常代表重复做几次的意思！ 也有可能是代表去到第几个什么什么的意思。

  举例来说，要删除 50 行，则是用 『50dd』 对吧！ 数字加在动作之前，如我要向下移动 20 行呢？那就是『20j』或者是『20↓』即可


## linux用户和权限

### root用户

- `su - root`切换root用户
- 普通用户一般在HOME目录内不受限
- ![image-20230911213137683](Linux.assets/image-20230911213137683.png)

sudo命令

- ![image-20230911213537754](Linux.assets/image-20230911213537754.png)
- 需要以root用户执行visudo命令，增加配置方可让普通用户有sudo命令权限

### 用户和用户组

以下命令需root用户执行

- 创建用户组`groupadd 用户组名`
- 删除用户组`groupdel 用户组名`

用户管理

![image-20230911221115849](Linux.assets/image-20230911221115849.png)

==ubuntu不会自动创建home文件夹，需加上-m==

getent passwd：查看当前系统中有哪些用户 

getent group ：查看用户组

### 查看权限控制

![image-20230911222639460](Linux.assets/image-20230911222639460.png)

![image-20230911222623108](Linux.assets/image-20230911222623108.png)

![image-20230911222715825](Linux.assets/image-20230911222715825.png)

### chmod命令

![image-20230912100236241](Linux.assets/image-20230912100236241.png)

![image-20230912101022942](Linux.assets/image-20230912101022942.png)

![image-20230912101113084](Linux.assets/image-20230912101113084.png)

### chown命令

可以修改文件所属用户或用户组

![image-20230912102413955](Linux.assets/image-20230912102413955.png)

## Linux实用操作

### 小技巧

- ctrl+c：强制停止
- ctrl + d：推出或登出（除了vi
- ctrl + r：关键字搜索历史命令
- ctrl + a：跳到开头
- ctrl + e：跳到结尾
- ctrl +箭头：移动一个单词
- ctrl + l：清空终端

### 软件安装

![image-20230912110646888](Linux.assets/image-20230912110646888.png)

### systemctl命令

![image-20230912111110933](Linux.assets/image-20230912111110933.png)

### 软链接

![img](Linux.assets/v2-9abd33350e3bcb401f379752874f9b52_r.jpg)

![image-20230912151548660](Linux.assets/image-20230912151548660.png)

### 日期和时区

![image-20230912152051014](Linux.assets/image-20230912152051014.png)

![image-20230912152406759](Linux.assets/image-20230912152406759.png)

### IP地址和主机名

可以使用ifconfig查询本机ip地址

域名解析

![image-20230912154408432](Linux.assets/image-20230912154408432.png)

### 网络请求和下载

ping

- `ping [-c num] ip或主机名`
- -c表示检查次数，默认是无限次检查

wget

- ![image-20230919133755793](Linux.assets/image-20230919133755793.png)

curl

- `curl [-O] url`
- -O用用于下载文件

### 端口

nmap

- 查看端口的占用情况
- `nmap 端口`

netstat

- `netstat -anp|grep 端口号`，查看指定端口的占用情况

### 进程管理

 ps

- ![image-20230919142423365](Linux.assets/image-20230919142423365.png)
- ![image-20230919142728136](Linux.assets/image-20230919142728136.png)

kill

- `kill [-9] 进程ID`
- -9表示强制关闭

### 主机状态监测

top

- 查看资源占用情况
- q或ctrl+c退出
- ![image-20230919144314680](Linux.assets/image-20230919144314680.png)
- ![image-20230919144701603](Linux.assets/image-20230919144701603.png)

df

- ![image-20230919144838281](Linux.assets/image-20230919144838281.png)

iostat

- ![image-20230919144903894](Linux.assets/image-20230919144903894.png)

sar

- 网络状态监控
- `sar -n DEV num1 num2`
- -n表示查看网络，DEV表示查看网络接口
- num1：刷新间隔。num2：查看次数

### 环境变量

env

- 查看当前环境变量

$

- 将环境变量中的键转换为值
- `echo $PATH`

配置环境变量

![image-20230919150334978](Linux.assets/image-20230919150334978.png)

![image-20230919151243236](Linux.assets/image-20230919151243236.png)

### 上传和下载

rz上传

sz下载

### 压缩和解压

![image-20230919152520661](Linux.assets/image-20230919152520661.png)

tar

- ![image-20230919152740795](Linux.assets/image-20230919152740795.png)

压缩

- ![image-20230919153049334](Linux.assets/image-20230919153049334.png)

解压

- ![image-20230919153715913](Linux.assets/image-20230919153715913.png)

zip

- ![image-20230919154052594](Linux.assets/image-20230919154052594.png)

unzip

- ![image-20230919154254691](Linux.assets/image-20230919154254691.png)

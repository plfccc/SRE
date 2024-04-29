## 	Day1 虚拟机的安装,xshell的连接

1. 虚拟机开机界面  输入命令

```shell
net.ifnames=0 biosdevname=0
```

[^作用]: 用于让网卡名字变成 ethx 形式 eth0 eth1

- 系统版本CentOS 7.9 内核3.10.0

# Day2

- **IP地址**

  - ip address # ip a

  - ip地址:设备的位置

  - 可分简单的为2类: 局域网IP(内网IP,私网IP),公网IP(外网IP)

- **端口**
  - 远程连接服务 ssh默认端口:22
  - 网站服务http :80
  - 网站服务加密https:443

- **协议**
  - 双方共同遵守的准则
  - 远程连接遵守的是ssh协议			

- **Linux常用快捷键**

| Linux快捷键        | 快捷点及说明 |
| ------------------ | ------------ |
| 光标移动到行首     | ctrl+a       |
| 光标移动到行尾     | ctrl+e       |
| 光标到行首内容剪切 | ctrl+u       |
| 光标到行尾内容剪切 | ctrl+k       |
| 清屏               | ctrl+l       |
| 取消当前命令       | ctrl+c       |
| :warning:锁屏      | ctrl+s       |
| 解锁               | ctrl+q       |
| :warning:挂起      | ctrl+z       |

># 总结

1. ip地址
2. 常用端口:22,80,443
3. 协议
4. 远程连接出错问题排除
   - 检查道路是否通畅:==Ping==
   - 是否有防火墙
   - 是否提供端口服务:==telnet==检查端口是否通畅
5. Linux常见快捷建

# Day3

> Linux 网卡配置文件的绝对路径：==/etc/sysconfig/network-scripts/ifcfg-eth0==

- ## 根下核心目录	

| 根下核心目录 | 描述                          |
| ------------ | ----------------------------- |
| :star:/etc/  | 系统服务配置文件              |
| :star:/home/ | 普通用户的家                  |
| :star:/root/ | 根用户的家                    |
| /dev         | device,设备文件目录，硬盘光盘 |
| :star:/tmp/  | 临时目录，存放临时信息        |
| /proc/       | peocess 系统服务，进程信息    |

- ## 路径

  - 绝对路径：从根开始
  - 相对路径：不从根开始

- ## 命令详解

  :one:

  | 命令 | 详解                                              |
  | ---- | ------------------------------------------------- |
  | cd   | change directory 进入到某个目录                   |
  | pwd  | print work directory 现实当前所在位置（绝对路径） |

  | cd命令的其他用法 |                |
  | ---------------- | -------------- |
  | cd ~ 或者cd      | 回老家         |
  | cd ..            | 回到上层目录   |
  | cd -             | 回到上一次目录 |

  :two::mkdir创建目录

  ​	-p :创建多个目录

  :three::touch 创建文件

  :four::ls 展示目录内容

  > -l:现实较多内容信息
  >
  > -t:按时间顺序显示
  

​	:five::mv 用来对文件或目录重新命名

​	:six::cp 复制拷贝

> -a 复制全部
>
> -t 反转源地址与目标地址 (可与|xargs使用)

​	:seven::echo 输出信息到屏幕 可与重定义符号>  或者追加符>>使用

​	:eight::cat 显示文件内容 也可2文件内容追加使用

```shell
  例: cat oldboy.txt demo1.
```

​	:nine::rm 用于删除给定的文件和目录

> -r: 递归处理，将指定目录下的所有文件与子目录一并处理
>
> -f: 强制删除文件或目录

- ## 优化yum源(方便下载安装)

  ```shell
  1:配置yum源	
  # curl -o /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-7.repo
  # curl -o /etc/yum.repos.d/epel.repo https://mirrors.aliyun.com/repo/epel-7.repo
  2:安装常用工具
  # yum install -y tree vim wget bash-completion bash-completion-extras lrzsz net-tools sysstat iotop iftop htop unzip nc nmap telnet bc psmisc httpd-tools bind-utils nethogs expect
  ```

- ## vi-vim编辑器详解

  ```sh
  vim  /demo1/demo.txt 
  ```

  > 文件不存在则会自动创建文件
  >
  > 目录不存在则不会创建,并报错

  - 进入编辑模式:  i

  - 推出编辑模式:  esc
  - 保存并退出:  :wq
  - 不保存强制退出: :q!

- ## 移动光标快捷键	:star::star::star::star:

  > 移动到最后一行  G(shift+g)
  >
  > 移动到第一行 gg
  >
  > 移动到某一行 xx gg(右边数字键不行)
  >
  >    
  >
  > 移动到行首：shift+^
  >
  > 移动到行尾：shift+$
  >
  >  
  >
  > 了解：   h(左)   l(右)   k(上)    j(下)

  

- ## 复制，删除，粘贴  :star::star::star::star:

> 复制当前行   yy
>
> 删除当前行（剪切） dd
>
> 粘贴  p

- ## 其他快捷键:star::star::star::star:

  > 撤销    u(undo)
  >
  > 显示行号    ：set nu
  >
  > 取消显示行号  ：set nonu
  >
  > 搜索   /（需要查找的内容）
  >
  > 继续向下搜索  n
  >
  > 继续向上搜索  N

  >  shift+v 进入到可视行模式（批量操作）
  >
  > 按上下键，选择要处理的范围
  >
  > 删除按d,复制按y 

- ## 故障案例

  - vim编辑文件故障提示

![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240221155709887.png)

-  原因：

  - vi/vim在编辑文件时会生成临时文件
  - 通过保存退出，隐藏文件会消失
  - 异常情况，断电，同时编辑这个文件，就会有这个提示

- 解决：

  - 1.删除临时文件，根据提示的路径删除对应的临时文件

  - 2.恢复文件

  - ```sh
    恢复流程
    vim -r demo.txt
    rm -f .demo.txt.swxxx
    重新打开文件即可恢复
    ```

    

# Day4服务 器

- ## 服务器概述

  - [服务器](https://link.zhihu.com/?target=https%3A//www.pangdayun.com/)**的英文名称为“ Server”，是指在网络上提供各种服务的高性能计算机。**作为网络的节点，存储、处理网络上80％的数据、信息，因此也被称为网络的灵魂

- ## 运维基操作

  - 修改&查看主机名： hostname ,hostnamectl

# Day5 查看日志四剑客

> 查看日志不要使用，cat，vim,vi命令。		

- Linux查询日志，文件较大，系统可能会卡死，内存不足

- 推荐使用不会占用系统太多资源的命令，查看日志：head/tail ,less/more

## 日志查询命令的使用  

- ### head 显示文件的头几行，默认是头10行 选项 -n  num显示头num 行

  ```sh
  案例01 显示/etc/passwd 的前5行
   head -n5 /etc/passwd
   head -n 5 /etc/passwd
   head -5 /etc/passwd
  ```

  > ⚠ 温馨提示:
  >
  > 一般情况下,使用-数字即可.如果-5报错或无法使用,则使用-n5
  >
  > 形式

- ### tail显示文件的后几行，默认是后10行

  | tail选项 |                      |
  | -------- | -------------------- |
  | -n num   | 显示最后num行        |
  | -f       | 实时显示文件末尾更新 |

  ```sh
  案例02 显示/etc/passwd 的后5行
  tail -n5 /etc/passwd
  tail -5 /etc/passwd
  ```

- ### less 按页显示文件内容

  > 一页一页显示文件内容也可也进行搜索

| less选项与快捷方式 | 说明                   |
| ------------------ | ---------------------- |
| q                  | 退出                   |
| 空格或f            | 下一页                 |
| b                  | 上一页                 |
| G                  | 最后一行               |
| g                  | 第一行                 |
| 99g                | 到99行                 |
| /内容              | 搜索，n继续向下，N向上 |
| less - n           | 显示行号               |

- ### more 按页显示文件内容到达最后一行就退出

  功能与less类似

- ## wc统计  :star::star::star::star::star:

> 选项： -l  统计行数

```sh
#案例 04 统计/etc/services文件有多少行
wc -l /etc/services
11176 /etc/services
```

```sh
案例05 统计系统用户登录错误次数
#1. 过滤出日志中错误信息
grep 'Failed password' /var/log/secure #过滤
Jul 19 09:32:44 oldboy-83-lnb-v2 sshd[7082]: 
Failed password for root from 10.0.0.1 port 
65157 ssh2
Jul 19 09:32:55 oldboy-83-lnb-v2 sshd[7082]: 
Failed password for root from 10.0.0.1 port 
65157 ssh2
#2. 交给wc -l 统计次数
grep命令的结果传递给wc -l命令。
grep 'Failed password' /var/log/secure | wc -l
2
```

> grep命令过滤，在文件中，命令结果中找出你要的内容.
>
> 管道符号
>
> 命令1 | 命令2 
>
> 把前一个命令的结果,传递给后面的命令使用
>
>  管道符号 |

## 排序去重组合⭐⭐⭐⭐⭐

- sort: 排序
- uniq: 去重	

- ### sort - 排序

  | sort选项 | 说明                           |
  | -------- | ------------------------------ |
  | -n       | 按照数字顺序排序               |
  | -r       | 逆序                           |
  | -k       | 指定某一列                     |
  | -t       | 指定分隔符==只能指定一个字符== |

  ```sh
  20k面试题-以.为分隔符对第3列和第4列排序.
  cat >/oldboy/sort-20k.txt<<EFO
  192.168.3.1 00:0F:AF:81:19:1F
  192.168.3.2 00:0F:AF:85:6C:25
  192.168.3.3 00:0F:AF:85:70:42
  192.168.2.20 00:0F:AF:85:55:DE
  192.168.2.21 00:0F:AF:85:6C:09
  192.168.2.22 00:0F:AF:85:5C:41
  192.168.0.151 00:0F:AF:85:6C:F6
  192.168.0.152 00:0F:AF:83:1F:65
  192.168.0.153 00:0F:AF:85:70:03
  192.168.1.10 00:30:15:A2:3B:B6
  192.168.1.11 00:30:15:A3:23:B7
  192.168.1.12 00:30:15:A2:3A:A1
  192.168.1.1 00:0F:AF:81:19:1F
  192.168.2.2 00:0F:AF:85:6C:25
  192.168.3.3 00:0F:AF:85:70:42
  192.168.2.20 00:0F:AF:85:55:DE
  192.168.1.21 00:0F:AF:85:6C:09
  192.168.2.22 00:0F:AF:85:5C:41
  192.168.0.151 00:0F:AF:85:6C:F6
  192.168.1.152 00:0F:AF:83:1F:65
  192.168.0.153 00:0F:AF:85:70:03
  192.168.3.10 00:30:15:A2:3B:B6
  192.168.1.11 00:30:15:A3:23:B7
  192.168.3.12 00:30:15:A2:3A:A1
  EOF
  指定分隔符，多列排序的时候容易出现排序失误。
  这时候需要我们手动告诉sort, 排序的范围.
  #以.为分隔符
  sort -t"."  -rn  -k3 sort-20k.txt
  sort -t"."  -rn  -k3,3  -k4,4 sort-20k.txt
  -rn 数字逆序排序
  -k3,3 表示仅对第3列排序
  -k4,4 表示仅对第4列排序
  ```

  详细案例：day06 

- ### uniq(处理附近2行)

​	选项：-c 去重并显示次数（重复次数）

```sh
案例09 统计secure-ip.txt文件中每个ip出现的次数并取出前5
1.通过sort处理下
2.去重uniq -c 
3.sort对次数进行排序
4.head取出5
sort secure-ip.txt |uniq -c |sort -rn |head -5 
68652 218.65.30.25
34326 218.65.30.53
21201 218.87.109.154
18065 112.85.42.103
17164 112.85.42.99
```

## 日期组合

- ### date

- ### ntpdate

- ### 特殊符号

  ## date

  >  设置或查看系统时间，时间命令
  >
  > 未来主要用于查看日期或者过去日期

  | date选项 |                          |
  | -------- | ------------------------ |
  | +        | 以xxxx格式显示时间与日期 |
  |          | %F（年-月-日） %Y- %m-%d |
  |          | %w 周几                  |
  |          | +%T %H:%M:%S 时分秒      |
  | -d       | 根据说明修改时间         |
  | -s       | 修改时间                 |

  ```sh
  #案例10 按照指定格式显示日期 年-月-日 2022-11-11
  date +%F
  2022-07-19
  full 可以理解为完整的日期
  ```

  ```sh
  #案例11 按照指定格式显示日期 年月日 20221111
  Year 
  month
  day 
  date +%Y%m%d
  20220719
  #案例12 显示当前时间 时:分:秒
  Hour
  Mintue 
  Second
  date +%T #T time 
  date +%H:%M:%S
  #案例13 显示当前日期为 年-月-日_周几
  date +%F_%w   #%w weekday
  2022-07-19_2
  ```

  ```sh
  [root@oldboy-king-v3 oldboyՎʠ date -d '-1 day'
  2022年 07月 18日 星期一 15:15:58 CST
  [root@oldboy-king-v3 oldboyՎʠ date -d '1 day'
  2022年 07月 20日 星期三 15:16:10 CST
  #案例14 显示1天的日期 按照年-月-日_周几_小时 格式显示
  date -d '-1day' +%F_%w_%H  
  2022-07-18_1_15
  ```

  ```sh
  date -s '20221111 11:11:11'
  date -s '20221111'
  ```

  

## 	ntpdate 同步时间命令

```sh

#修改系统时间，让系统时间不同步.
date -s '20221111'
#安装时间同步命令
yum install -y ntpdate
#进行时间同步
ntpdate ntp1.aliyun.com 
19 Jul 15:26:13 ntpdate[7937]: step time server 
120.25.115.20 offset -9880664.037056 sec
#最后检查
date命令查看时间
提示offset xxx sec表示同步成功
```



> 特殊符号：`` ,反引号里的命令会被有限执行

```sh
date +%F
touch backup-etcxxxxx.txt
touch backup-etc-`date +%F'.txt
ls -l backup-etc-2022-07-19.txt
```



- ## linux文件属性

 ![](D:\电脑管家迁移文件\WeChat Files\wxid_yhnsz6whnawl21\FileStorage\Temp\1708589997473.png)

- inode于block部分

  - inode索引节点,inode号码类似于身份证号码,通过inode号码

    可以找到文件的内容.

  -  inode是一个空间，inode号是空间的位置,类似于身份

    证,inode空间存放:

    ​	inode空间中存放的是 文件属性信息 ,文件大小,修改

    ​	时间,权限,所有者

    ​	inode空间中存放block的位置(指向文件实体的指针)

    ​	这里不存放文件名.

  ​	⭐ block块(数据块): 存放数据

  - Inode和block的关系

<img src="D:\电脑管家迁移文件\WeChat Files\wxid_yhnsz6whnawl21\FileStorage\Temp\1708589899811.png" style="zoom:80%;" />

### 	用户访问查看oldboy.txt文件内容的流程:

​		1.用户访问oldboy.txt的时候，系统会找出他对应的

​		inode空间（根据inode号码)。

​		2.访问来到inode空间后，确认用户,确认权限。

​		3.权限信息正确就准许通过，可以访问inode对应的

​		block区域（数据）。

### 	inode和block特点

​		inode索引节点，存放文件属性信息，block位置



### 	查看

​	==df -h==：查看block的使用情况（磁盘空间）

​	==df -i==:查看inode的使用情况

​	==ll -h==:查看文件大小

​	==du -sh==查看目录所占空间

> ==课外小知识:== 文件名是存放在目录的block中的. 没有存放在
>
> inode中,所以文件名不是文件属性

Linux文件类型 	:star2::star2:

| Linux常见文件类型 | 含义                                 |
| ----------------- | ------------------------------------ |
| -                 | 文件范围，范围广                     |
| d                 | 目录                                 |
| l                 | 软连接，类似于Windows快捷方式        |
| b                 | 块设备                               |
| s                 | socket文件                           |
| p                 | 管道文件                             |
| c                 | 字符设备 char 特殊文件,不断输出,吸入 |

> 可用 file 命令查看详细文件类型

## **软硬链接** ⭐⭐⭐⭐⭐

- ### 概述

  - 软：类似于windows中快捷方式,也是一种文件;用于存放源

    文件的路径(位置+名字),应用最多.

  - 硬：在同一个分区中,不同的文件的inode号码相同了,这些

    文件互为硬链接,很少使用.

- ### 创建

  - ==ln(link)命令==

    ```sh
    ln -s 创建软连接
    ln 创建硬连接
    
    ln -s oldboy.txt oldboy.txt_soft
    
    ```

    

## 打包压缩

| 压缩命令    | 应用           |
| ----------- | -------------- |
| tar:star:   | 大部分应用场景 |
| gzip        | 一般           |
| zip，unizip | 一般           |

### tar :star::star::star:

- 打包（将文件放到一起）tar命令
- 压缩（进行压缩，节约空间）tar命令的一些选项

| tar命令  | 选项与说明                            |
| -------- | ------------------------------------- |
| 创建 zcf | tar zcf 压缩包 被压缩的文件/目录 .... |
| 查看 tf  | tar tf /tmp/etc.tar.gz                |
| 解压 xf  | tar xf /tmp/etc.tar.gztar             |

### 解压到指定目录

```sh
解压etc.tar.gz 到/mnt目录下
-C解压到指定目录
tar xf 压缩包 -C 解压后的存放目录
tar xf /tmp/etc.tar.gz -C /mnt/
```





# 四剑客-grep ⭐⭐⭐⭐⭐

- 过滤:在文件中或管道中进行查找,找出想要的内容（字符串），

  默认按照行查找

- grep会把匹配到的行显示出来.

> 补充：4剑客
>
> ==awk,sed,grep,find==

| grep选项 | 选项及内容       |
| -------- | ---------------- |
| -n       | 显示所在行号     |
| -i       | 不区分大小写过滤 |
| -v       | 排除，取反       |

```sh
grep 'root' /etc/passwd
root:x:0:0:root:/root:/bin/bash
operator:x:11:0:operator:/root:/sbin/nologin

```

```sh
grep -n 'ssh' /etc/services 
46:ssh             22/tcp                          # The Secure Shell (SSH) Protocol
47:ssh             22/udp                          # The Secure Shell (SSH) Protocol
552:x11-ssh-offset  6010/tcp                        # SSH X11 forwarding offset
592:ssh             22/sctp                 # SSH

```

# 四剑客-find⭐⭐⭐⭐⭐

- 擅长查找

| find选项 | 详细解释                             |
| -------- | ------------------------------------ |
| -type    | 查找类型  f：文件 d：目录            |
| -name    | 文件名                               |
| -size    | 根据大小查找文件 大于使用+ 小于使用- |
| -mtime   | +7 :7天之前的   -7：最近7天          |

```sh
#案例01 在/etc/目录中找出文件名叫hostname文件
精确查找，指定文件名。
find /etc/   -type f  -name 'hostname'
/etc/hostname
#案例02 找出/etc/下面以.conf结尾的文件
模糊查找
a.conf b.conf c.conf lidao.conf xxxx.conf 
find /etc/ -type f -name '*.conf'

```

## 综合案例

```sh
#案例05 找出/etc/中以.conf结尾大于10kb修改时间是7天之前
的文件
find /etc/ -type f -name '*.conf' -size +10k  -
mtime +7
/etc/lvm/lvm.conf
[root@oldboy83-prod ~]# ls -lh /etc/lvm/lvm.conf 
-rw-r--r--. 1 root root 94K 10月  1 2020
/etc/lvm/lvm.conf
```

```sh
#案例06 查找文件的时候指定最多找多少层目录.
find / -maxdepth 2 -type f -name '*.conf'
/etc/resolv.conf
/etc/asound.conf

-maxdepth 1 选项位置第1个，指定find命令查找的最大深度
（层数），不加上就是所有层。

#案例07 查找的时候不区分文件名的大小写
find /   -type f -iname "*.conf"

```

## find命令于其他命令配合

> ==find与|xargs使用时候find找到的文件某人放在下一个命令后面==

- find+简单命令 ：find找出想要的文件删除,看详

  细信息，显示文件内容，过滤。

- find+打包压缩： find找出文件进行打包压缩

- find+cp/mv:find找出文件后复制或移动

### 找出/oldboy/find/以.txt结尾的文**件显示详细信息**⭐⭐⭐

> 这里主要用到find+ls配合，后面的其他配合find+rm，
>
> find+cat/head/tail/，find+grep都类似。
>
> find不要与交互式命令配合find+vi/vim ❌

- 方法01 find  ``⭐ ⭐ ⭐ ⭐ ⭐ 

> find与其他命令配合必会方法 find + 反引号+其他命令

```sh
ls -lh find命令的结果
ls -lh `find /oldboy/find/ -type f -name 
'*.txt'`
ls -lh $(find /oldboy/find/ -type f -name 
'*.txt')
先运行find命令找出文件，然后运行ls显示文件详细信息。
```

- 方法02 find |xargs ⭐ ⭐ 

  > 我们发现find命令使用管道把数据传输给其他命令失败了！！！
  >
  > find /oldboy/find/ -type f -name "*.txt" | ls -l
  >
  > 无法使用。
  >
  > 关于管道的秘密:
  >
  > find /oldboy/find/ -type f -name '*.txt' | ls-lh
  >
  > ls 选项 参数
  >
  > 错误的心路历程：默认管道是无法把数据变化为命令的参数，导致传递失败，find
  >
  > 命令找出的内容相当于被丢弃了，就相当于执行ls -lh命令，显示当
  >
  > 前目录下内容并详细信息。
  >
  > 故障原因:
  >
  > 前面的命令通过管道传递给后面命令,传递的是 字符串 .
  >
  > 这个命令(ls)中传递文字符号就不行,传递 参数 .
  >
  > 所以上面的命令相当于find白白浪费了,仅仅执行了下ls -lh而已 .
  >
  > 如何解决:
  >
  > 通过|xargs把前面命令传递过来的字符串转换为后面命令可以识
  >
  > 别参数.

```sh
效果展示：
find /oldboy/find/  -type f  -name '*.txt' |xargs 
 ls -lh
```

##   find与打包压缩

- find找出/oldboy/find/ 以.txt结尾的文件放在/tmp/find.tar.gz 

法1 find ``

```sh
tar zcf /tmp/find.tar.gz  `find /oldboy/find/ -
type f -name '*.txt'`
```

法2 find + |xargs

```sh
find /oldboy/find/  -type f  -name '*.txt'|xargs 
tar zcf /tmp/etc-xargs.tar.gz
```

法3 find +exec

```sh
find /oldboy/find/  -type f  -name '*.txt'  -exec 
tar zcf /tmp/find-exec.tar.gz {} \;
有坑,因为-exec \;执行方式 1个文件1个文件的压缩.
find /oldboy/find/  -type f  -name '*.txt'  -exec 
tar zcf /tmp/find-exec.tar.gz {}  +
```



## find与复制或移动

- find找出/oldboy/find/ 以.txt结尾的文件然后复制到/tmp下面

法1 find +``

```sh
cp `find /oldboy/find/ -type f -name '*.txt'` /tmp/
```

法2 find+|args

```sh
find xxx   |xargs cp /tmp/
运行的时候
1. find找出文件 oldboy01 ՎՎʢ oldboy10 
2. 把10个文件传输给cp命令
3. cp /tmp/ oldboy01 ՎՎʢ oldboy10 
cp -t /tmp/ oldboy01 ՎՎʢ oldboy10  
cp -t 目标   源 文件 目录 ..... 
如何解决
find /oldboy/find/  -type f  -name '*.txt'
|xargs cp -t /tmp/
```

方法03 find + -exec 

```sh
find /oldboy/find/  -type f  -name '*.txt' -exec 
cp {} /tmp/ \;
```



# 别名与用户管理系统



查看别名 :==alias==

## 设置别名

```sh
alias rm='echo rm command is not found'
#设置别名
alias 昵称='命令'
alias rm 
alias rm='echo rm command is not found'
```

> 如果想真的删除文件(临时取消别名):
>
> 🅰 使用命令绝对路径 /bin/rm 
>
> 🅱 使用撬棍(反斜线) \别名

```sh
 \rm /oldboy/oldboy.txt
```

## 永生

> 一般命令行的操作都是临时，重启或重新登录失效了。
>
> 这时候我们要记得让配置永久生效，修改配置文件。
>
> 修改配置文件 ~/.bashrc（当前用户生效） 
>
> /etc/profile（全局cat）
>
> 关于井号# 表示注释，#号之后的内容系统认为不存在，会忽略掉。
>
> 关于别名生效：重新登录即可，断开连接然后重新连接。
>
> \#修改/etc/profile 
>
> 在最后一行写入配置别名的命令。



```sh
#修改/etc/profile 
#修改配置文件 ~/.bashrc（当前用户生效） 
在最后一行写入配置别名的命令。
alias rm='echo rm command is not found'
#让配置文件生效（source目前仅用于profile文件）
source /etc/profile
#检查别名
alias  rm 
alias rm='echo rm command is not found'
#未来除了rm,cp,mv命令的别名，配置到此为止。
对于rm,cp,mv命令的别名，还要额外配置下，否则不生效。
#注释掉~/.bashrc里面已经配置的别名
修改~/.bashrc 注释#alias rm='rm -i' 这一行
#检查注释结果
[root@oldboy-lnb-king-v3 ~]# grep 'rm' ~/.bashrc
#alias rm='rm -i
```





# 用户管理 

| 用户分类 | 分类方法                                           |
| -------- | -------------------------------------------------- |
| root     | uid是0                                             |
| 普通用户 | uid>=1000(C7之后）                                 |
| 虚拟用户 | uid <1000, 也叫傀儡用户, 用于服务,进程运行使用的用 |

> 提示：uid是分类的1中方法

## 用户相关的文件

> Linux下每创建一个用户，一般会影响下面几个文件

| 用户相关文件 |                              |
| ------------ | ---------------------------- |
| /etc/passwd  | 存放用户信息                 |
| /etc/shadow  | 存放密码信息                 |
| /etc/group   | 用户组信息                   |
| /etc/gshadow | 用户组密码信息，几乎不会设置 |

- /etc/passwd 每一列含义

  ![](D:\电脑管家迁移文件\WeChat Files\wxid_yhnsz6whnawl21\FileStorage\Temp\1708617277163.png)

## 用户管理指令

- ### 增加useradd

  | ueradd选项 | 说明                            |
  | ---------- | ------------------------------- |
  | -u         | 指定用户uid                     |
  | -s         | 指定命令解释器，默认是/bin/bash |
  | -M         | 不创建家目录                    |

  ```sh
  #添加用户 oldboy 
  useradd oldboy 
  grep 'oldboy' /etc/passwd
   -s /sbin/nologin -M   mysql 
  [root@oldboy-lnb-king-v3 ~]# grep 'mysql' 
  /etc/passwd /etc/group /etc/shadow
  /etc/passwd:mysql:x:1314:1314::/home/mysql:/sbin
  /nologin
  /etc/group:mysql:x:1314:
  /etc/shadow:mysql:!!:19331:0:99999:7ՎՎʧ
  
  
  id mysql 
  uid=1314(mysql) gid=1314(mysql) 组=1314(mysql)
  ```

  - ### 修改密码 passwd

    | passwd选项 | 说明             |
    | ---------- | ---------------- |
    | --stdin    | 非交互式设置密码 |

  - ### 切换用户   su-

```sh
su - oldboy
#退出当前用户
ctrl + d #相当于logout命令
su switch user 切换用户。
```

> ⚠ 温馨提示: 关于su - 与su命令
>
> su命令中的-,是su命令的选项: -, -l, Վʔlogin
>
> 切换用户的时候,更新用户的配置与环境变量。

- ### 删除 userdel

  | userdel选项 |                  |
  | ----------- | ---------------- |
  | -r          | 删除用户及家目录 |

  ```sh
  删除用户 mysql 
  userdel mysql
  grep 'mysql' /etc/passwd
  彻底删除用户包含家目录
  [root@oldboy-king-v2 ~]# ll -a /home/oldboy 
  总用量 16
  drwx------. 2 oldboy oldboy  83 7月  22 10:50 .drwxr-xr-x. 3 root   root    20 7月  22 10:28 Վʡ
  -rw-------. 1 oldboy oldboy  70 7月  22 11:03 
  .bash_history
  -rw-rՎʔrՎʔ. 1 oldboy oldboy  18 4月   1 2020
  .bash_logout
  -rw-rՎʔrՎʔ. 1 oldboy oldboy 193 4月   1 2020
  .bash_profile
  -rw-rՎʔrՎʔ. 1 oldboy oldboy 231 4月   1 2020
  .bashrc
  [root@oldboy-king-v2 ~]# userdel -r oldboy 
  [root@oldboy-king-v2 ~]# ll -a /home/oldboy 
  ls: 无法访问/home/oldboy: 没有那个文件或目录
  [root@oldboy-king-v2 ~]# grep oldboy /etc/passwd
  ```

  - ### 查看

    -  id 查询用户的uid,gid,用户组信息,检查用户是否存在
    - whoami 查询当前用户的名字
    - w 查看当前登录的用户的信息
    - last 用户的登录情况
    - lastlog 所有用户最近1次登录情况
  
  ```sh
  #id 查看用户id信息 uid gid 属于的用户组 判断用户是否存在
  2 [root@oldboy-lnb-king-v3 ~]# id oldboy
  3 uid=1000(oldboy) gid=1000(oldboy) 组=1000(oldboy)
  4 [root@oldboy-lnb-king-v3 ~]# usermod -G root oldboy   #让oldboy用户属于oldboy组和root组
  5 [root@oldboy-lnb-king-v3 ~]# id oldboy
  6 uid=1000(oldboy) gid=1000(oldboy) 组=1000(oldboy),0(root)
  7 [root@oldboy-lnb-king-v3 ~]# usermod -G '' oldboy     #把oldboy从root组踢出
  8 [root@oldboy-lnb-king-v3 ~]# id oldboy
  9 uid=1000(oldboy) gid=1000(oldboy) 组=1000(oldboy)
  ```
  
  ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240223140823065.png)



### sudo 授权于管理

```sh
#root授权配置
visudo   = 背后修改 vi /etc/sudoers 
#普通用户使用
sudo + 命令

#root用户授权
visudo   = vim /etc/sudoers
第100行后面
oldboy  ALL=(ALL)     /bin/cat, /bin/head, /bin/tail, /bin/less, /bin/more, 
/bin/grep
#过滤检查配置结果
grep oldboy /etc/sudoers
#oldboy使用
sudo head /var/log/secure
[sudo] oldboy 的密码：  #输入oldboy密码
#查看普通用户拥有的sudo权限.
sudo -l 查看当前用户有什么sudo权限,关注最后2行即可
```

> 运维自己使用的普通用户  

```sh
lidao996 ALL=(ALL)     NOPASSWD: ALL
grep lidao996 /etc/sudoers
```

## 小结

- 为何使用sudo? 以普通用户权限进行管理，拥有部分的root权限
- 如何用？root进行授权:visudo 普通用户下面进行使用：sudo 命令。
- 未来还有别的方案可以用（堡垒机）。	



# 堡垒机与跳板机

![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240223145557484.png)

## 堡垒机搭建过程

```sh

#下载软件包
从群文件下载，并上传到Linux即可。
#检查文件大小  
[root@oldboy-lnb-king-v3 ~]# ll -h teleport-server-linux-x64-3.6.4-b3.tar.gz
-rw-r - r - . 1 root root 32M 12月  6 15:21 teleport-server-linux-x64-3.6.4-b3.tar.gz
#解压
[root@oldboy-lnb-king-v3 ~]# tar xf teleport-server-linux-x64-3.6.4-b3.tar.gz
[root@oldboy-lnb-king-v3 ~]# ll
。。。。。。中间结果略过。。。。。。
drwxr-xr-x. 5 oldboy oldboy       62 9月  13 10:07 teleport-server-linux-x64-3.6.4-b3
-rw-r - r - . 1 root   root   32717761 12月  6 15:21 teleport-server-linux-x64-3.6.4-
b3.tar.gz
#进入目录并安装
 cd teleport-server-linux-x64-3.6.4-b3/
 ./setup.sh
#根据提示进行安装
[]===========================================================================[]
 | Teleport Server Installation                                             |
 |===========================================================================|
 |   ver: 3.6.4                                                             |
 | author: apex.liu@qq.com                                                   |
[]===========================================================================[]
Welcome to install Teleport Server!
NOTICE: There are a few steps need you enter information or make choice,
        if you want to use the DEFAULT choice, just press `Enter` key.
       Otherwise you need enter the highlight character to make choice.
Prepare installation .
 - check local installation . [not exists]
Set installation path [/usr/local/teleport]:   直接回车即可，除非像安装到其他目录下面。
 - copy [/root/teleport-server-linux-x64-3.6.4-b3/data/bin]
     -> [/usr/local/teleport/bin]
 - copy [/root/teleport-server-linux-x64-3.6.4-b3/data/www]
     -> [/usr/local/teleport/www]
 - copy [/root/teleport-server-linux-x64-3.6.4-b3/data/tmp/etc]
     -> [/usr/local/teleport/data/etc]
process [daemon.in] to [/etc/init.d/teleport]
process [start.sh.in] to [/usr/local/teleport/start.sh]
process [stop.sh.in] to [/usr/local/teleport/stop.sh]
process [status.sh.in] to [/usr/local/teleport/status.sh]
start services .

starting teleport web . [done]
starting teleport core server . [done]
check services status .
teleport web server is running.
teleport core server is running.
=
[ ALL DONE ] = - #全部完成安装。
#检查teleport是否运行中。
/etc/init.d/teleport status #检查是否运行
teleport web server is running.  #ok
teleport core server is running. #ok
关闭或重启服务
/etc/init.d/teleport  stop #关闭服务
/etc/init.d/teleport  start #开启
/etc/init.d/teleport  restart #重启

#关闭防火墙
systemctl stop firewalld 
systemctl disable firewalld 
#检查防火墙是否关闭
systemctl status firewalld 
不显示绿色（running)即可。
#关闭selinux(工作中基本关闭)
setenforce 0 #临时关闭
vim /etc/selinux/config  
找出中间的行SELINUX=enforcing 修改为 SELINUX=disabled
getenforce #结果是permissive或disabled都表示关闭。
           #如果是enforcing表示开启
```



#  **Linux12**位权限管理体系

- ## 概述

  - Linux通过rwx3种权限控制系统与保护系统,组成9位权限.
  - Linux权限体系中还有3位特殊权限,组合起来就是12位权限体系
  - Linux这简单的rwx控制整个Linux系统的安全,权限与用户共同组成Linux系统的安全防护体系.

  ## rwx

  | 权限 | 含义                                 |
  | ---- | ------------------------------------ |
  | r    | read是否可读                         |
  | w    | write 是否可写                       |
  | x    | execute 是否可执行(一般是命令或脚本) |

  ## 为何为9位权限

  | **文件**目录与用户的关系 | **含义**                                                    |
  | ------------------------ | ----------------------------------------------------------- |
  | 所有者                   | 这个文件或目录属于某个用户(所有者)。你自己                  |
  | 用户组(家庭)             | 这个文件或目录属于某个用户组(家庭)。家人。                  |
  | 其他人(陌生人)           | 这个文件或目录不属于某个用户 也不属于这个用户组。隔壁老王。 |

  

![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240223163216103.png)



![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240223163308120.png)

## **如何计算权限** ⭐️⭐️⭐️⭐️⭐

| **权限** | **含义**                            | **权限对应的数字** |
| -------- | ----------------------------------- | ------------------ |
| r        | read 是否可读                       | 4                  |
| w        | write 是否可写                      | 2                  |
| x        | execute 是否可执行(一般是命令,脚本) | 1                  |
| -        | 没有权限                            | 0                  |

```sh
-rw-r - r - .  1 root root    0 7月  18 08:53 oldboy01.txt
420400400
6  4  4
oldboy01.txt的权限是644
```

案例

```sh
字母 > 数字
-rwxr-xr-x 755   
-r - r - r - 444  
-r - rw-rw- 466  
数字 > 字母（文件）
644   -rw-r --r--
750   -rwxr-x 
700   -rwx------
600   -rw-------
```



## 修改权限

chmod命令: change mode 使用数字或字母形式修改权限。

chown命令：change owner 修改文件所有者，用户组

```sh

#修改oldboy.txt的权限为755.
chmod 755 oldboy.txt 
#修改oldboy.txt所有者和用户组为oldboy(存在)。
chown oldboy.oldboy oldboy.txt
```

## 文件和目录权限小结 ⭐️⭐️⭐️⭐️⭐

| 权限 | 文件                                           | 目录                                                         |
| ---- | ---------------------------------------------- | ------------------------------------------------------------ |
| r    | 是否可以读取文件内容(r)                        | 是否可以查看目录内容,需要x权限配合(rx)                       |
| w    | 是否可以修改文件内容,一般还需要r权限配合.(rw)  | 是否可以在目录中创建,删除,重命名文件权限,需要rx权限配合(rwx) |
| x    | 是否可以执行文件,(命令,脚本),一般还需要r权限配 | 是否可以进入目录,是否可以访问目录下文件属性(rx,rwx)          |





# 系统管理之软件包管理

- 软件安装方式推荐

​	:one:yum 优先

​	:two:rpm包

​	:three:二进制

​	:four:编译安装

## rpm安装方式

| **rpm**命令 | **选项及含义**                                  |
| ----------- | ----------------------------------------------- |
| 增加-安装   | -ivh (-i install ) xxxx.rpm                     |
| 查看-检查   | -qa (query all) 查看软件包是否安装              |
|             | -ql 查看软件包内容                              |
|             | -qf 文件或命令绝对路径 文件或命令所归属的软件包 |
| 修改-升级   | -Uvh 升级软件包(如果软件包不存在,相当是ivh安装) |
| 删除        | -e 删除软件包                                   |

## 增加-安装rpm包⭐️⭐️⭐️⭐️⭐️

> -ivh 
>
> -i install 
>
> -v 显示过程
>
> -h 人类可读显示过程

```sh
案例01 安装rpm包
#下载软件包
wget   - no-check-certificate -P /server/tools/ 
https: / mirrors.tuna.tsinghua.edu.cn/zabbix/zabbix/6.0/rhel/7/x86_64/zabbix-agent2-6.0.0-1.el7.x86_64.rpm
wget下载指定内容，默认下载到当前目录
-P 下载到指定目录，目录不存在会创建
no-check-certificate 下载地址https,加上这个选项，下载失败。
#安装依赖（后面yum部分可以解决软件包依赖和查找依赖）
yum install  -y pcre2
#安装软件包zabbix-agent2 
rpm -ivh zabbix-agent2-6.0.0-1.el7.x86_64.rpm
```

## 查询⭐️⭐️⭐️⭐️⭐️

```sh
#书写方法 利用管道+grep进行过滤 推荐
rpm -qa |grep zabbix 
#不使用管道 直接写软件包的名字
rpm -qa zabbix-agent2

#检查软件包的内容(已经安装)
rpm -ql  #list 
rpm -ql 软件
rpm -ql zabbix-agent2
```

## 升级 :star:

```sh

wget   -P /server/tools/ 
https: / mirrors.tuna.tsinghua.edu.cn/zabbix/zabbix/6.0/rhel/7/x86_64/zabbix-agent2-
6.0.7-1.el7.x86_64.rpm
[root@oldboy-lnb-king-v3 ~]# rpm -Uvh /server/tools/zabbix-agent2-6.0.7-
1.el7.x86_64.rpm
警告：/server/tools/zabbix-agent2-6.0.7-1.el7.x86_64.rpm: 头V4 RSA/SHA512 Signature, 
密钥 ID a14fe591: NOKEY
准备中 .                          ################################# [100%]
正在升级/安装 .
   1:zabbix-agent2-6.0.7-1.el7        ################################# [ 50%]
正在清理/删除 .
   2:zabbix-agent2-6.0.0-1.el7        ################################# [100%]
[root@oldboy-lnb-king-v3 ~]# rpm -qa |grep zabbix 
zabbix-agent2-6.0.7-1.el7.x86_64
```



## 删除

```sh
rpm -e 软件包
rpm -e zabbix-agent2
rpm -qa |grep zabbix
```

# yum软件包管理

- yum是红帽系列系统中默认的软件包管理器。替我们下载指定的rpm包,替我们安装，安装过程中有依赖，下载安装依赖
- 推荐安装,命令增强补全工具

## yum安装软件全流程

​	1️⃣运行yum install -y tree命令。

​	2️⃣解析下tree软件包是否有依赖。

​	3️⃣yum根据本地配置的yum源的地址，进行请求（相关软件包tree,依赖软件包）。

​	4️⃣如果yum源存在软件，则会通知yum进行下载，rpm包就被下载到yum缓存目录中。

​	5️⃣软件包和依赖（如果有）都下载OK，则开始安装。

​	6️⃣ 安装完成删除刚刚下载的rpm包（默认）。

## yum源配置⭐️⭐️⭐️⭐️⭐

- ### 一键配置为阿里云的yum源

  - 查看系统正在使用的源列表

    ```sh
    yum repolist	
    ```

    > ==源标识==              		==源名称==                                                       ==状态==
    > base/7/x86_64       CentOS-7 - Base - mirrors.aliyun.com              10,072
    > epel/x86_64         Extra Packages for Enterprise Linux 7 - x86_64    13,787
    > extras/7/x86_64     CentOS-7 - Extras - mirrors.aliyun.com               519
    > updates/7/x86_64    CentOS-7 - Updates - mirrors.aliyun.com            5,760
    > repolist: 30,138
    >
    > 目前这里可以看出有base,extras,updates,epel4个yum源
    >
    > base,extras,updates是系统默认的yum源
    >
    > epel是额外yum源

  - 设置系统的yum源为阿里云

    > https: / mirrors.aliyun.com/进入网站选择centos 
    >
    > 1. 备份已有yum源的配置文件
    >
    > mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
    >
    > 2. 配置系统默认的源，改为阿里云的。
    >
    > 使用wget或curl 下载阿里云的yum源的配置文件到/etc/yum.repos.d/目录下
    >
    > wget -O /etc/yum.repos.d/CentOS-Base.repo https: / mirrors.aliyun.com/repo/Centos-
    >
    > 7.repo-O 下载并改名，存放到指定目录中。
    >
    > 3. 修改了base,extras,updates是系统默认的yum源，改为了阿里云。

  - 增加epel源

    > \#1. 备份（第1次使用，提示文件不存在）
    >
    > mv /etc/yum.repos.d/epel.repo /etc/yum.repos.d/epel.repo.backup
    >
    > mv /etc/yum.repos.d/epel-testing.repo /etc/yum.repos.d/epel-testing.repo.backup
    >
    > \#2. 增加系统的epel源（企业级Linux的额外的软件包 yum仓库）
    >
    > wget -O /etc/yum.repos.d/epel.repo https: / mirrors.aliyun.com/repo/epel-7.repo
    >
    > \#3. 检查
    >
    > yum install -y sl cowsay 	

- ## yum源配置文件详解

  - ### 存放在/etc/yum.repos.d/目录下面，都是以.repo结尾，只能识别以.repo结尾的文件。

![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240224001855519.png)

- ### 配置文件格式

  ```sh 	
  [base] 这个源的名字
  name=CentOS-$releasever - Base - mirrors.aliyun.com
  failovermethod=priority
  baseurl=http: / mirrors.aliyun.com/centos/$releasever/os/$basearch/
         http: / mirrors.aliyuncs.com/centos/$releasever/os/$basearch/
         http: / mirrors.cloud.aliyuncs.com/centos/$releasever/os/$basearch/
  gpgcheck=1
  gpgkey=http: / mirrors.aliyun.com/centos/
  ```

  | yum源文件详解 |                                                       |
  | ------------- | ----------------------------------------------------- |
  | [base]        | yum源的名字                                           |
  | name=         | 说明信息                                              |
  | baseurl=      | yum源地址,打开后要看到repodata目录,这是yum配置的核心. |
  | enabled=1     | 是否开启这个yum源                                     |
  | gpgcheck=1    | 开启软件包检查,未来自建yum仓库可以关闭.               |
  | gpgkey        | 用于检查的秘钥. 如果关闭检查gpgkey省略.               |

- ### yum命令配置文件

  - 修改/etc/yum.conf配置，找出keepcache行=0改为=1即可.

  | /etc/yum.cof yum命令的配置文件 | 说明                                                         |
  | ------------------------------ | ------------------------------------------------------------ |
  | keepcache                      | =0关闭缓存，软件下载安装后自动删除rpm包。=1开启缓存，软件下载安装后保留rpm包。（自建yum源） |
  | cachedir                       | yum下载软件包的缓存目录，/var/cache/yum/$basearch/$releasever |
  | logfile                        | yum命令的记录 /var/log/yum.log                               |

- ### yum命令详解⭐️⭐️⭐️⭐️⭐️

​	

| yum命令 | 格式与说明                      |
| ------- | ------------------------------- |
| **增**  | **yum install -y tree**         |
| 查      | **yum provides** **内容**       |
|         | yum search all 内容             |
|         | **yum repolist** **查看源列表** |
| 删除    | yum remove 删除软件包及依赖     |
|         | yum clean all 清空缓存          |
| 改      | yum update/upgrade              |
| 选项    | -y 遇到有yes/no的时候选择yes    |

==通常情况下是用yum 命令下载，rpm -qa 检查安装==

# 系统管理体系之进程管理

- ## 进程

| 名字       | 含义                                                  |
| ---------- | ----------------------------------------------------- |
| 程序       | 安装包，程序代码，app                                 |
| 进程:star: | 运行起来的程序，命令，服务（远程连接）....,运行在内存 |
| 守护进程   | 守护进程，一直运行的进程，也可叫做服务                |

- ## 分类

  - ==僵尸进程==

    指的是当子进程比父进程先结束，而父进程又没有回收子进程，释放子进程占用的资源，此时子进程将成为一个僵尸进程。

​		查找:未来通过ps aux 过滤 Z状态可找出僵尸进程或top命令查看

​		解决:找出僵尸进程上级进程结束即可

​		若上级进程为主进程(pid=1),主进程重启Linux,其他进程结束这个进程

​	    ==孤儿进程==

​		孤儿进程指的是在其父进程执行完成或被终止后仍继续运行的一类进程			

​		孤儿进程会被系统直接接管.(systemd进程)

- ## 解决过程展示

  - top命令查看是否有僵尸进程

  - 过滤出僵尸进程

    ```sh
    ps aux |grep Z #找出僵尸进程的pid
    USER       PID %CPU %MEM   VSZ   RSS TTY     STAT START   TIME COMMAND
    root       2188  0.0  0.0      0     0 pts/0   Z+   10:04   0:00 [zombine] <defunct>
    root       2191  0.0  0.0 112824   960 pts/1   R+   10:05   0:00 grep -color=auto Z
    发现僵尸进程的pid是2188
    ```

  - pstree -p查看僵尸进程的父进程(上级进程)

    ```sh
    pstree -p |grep 2188
               ├─sshd(1344)─┬─sshd(1641)───bash(1643)───zombine(2187)───zombine(2188)
    ```

  - 结束僵尸进程的父进程

    ```sh
    kill 2187
    ```

- ## 进程监控命令⭐️⭐️⭐️⭐️⭐

  | 监控命令 | 含义                                                         |
  | -------- | ------------------------------------------------------------ |
  | ps       | 静态：ps查看当前瞬间进程状态,一般用于临时检查或取值.         |
  | top      | 动态：top动态,交互,整体查看系统状态,负载,僵尸进程,cpu,内存. 类似于windows任务管理器. |

  - ## 概述

    - ps -ef

    - ps -aux

      ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240225133913581.png)

- ## 进程状态

  - 进程状态:进程运行中，僵尸进程，正在进行io的进程，前台或后台运行进程。(基本状态+附加组成。)

  | **STAT**基本状态 | **描述**                         |
  | ---------------- | -------------------------------- |
  | S                | 可中断进程(可以随时停止)         |
  | **T(terminate)** | 进程被暂停(挂起) ctrl +z         |
  | **D**            | 不可中断进程(进程正在进行IO读写) |
  | **Z(zombie)**    | 僵尸进程，异常的进程             |
  | R(running)       | 运行中                           |

  | **STAT**状态**+**符号(附加状态)了解 | **描述**                                              |
  | ----------------------------------- | ----------------------------------------------------- |
  | **s**                               | 进程是**控制进程**， Ss进程的领导者，**父进程**主进程 |
  | <                                   | 进程运行在**高优先级**上，S<优先级较高的进程          |
  | N                                   | 进程运行在**低优先级**上，SN优先级较低的进程          |
  | **+**                               | **当前进程运行在前台**，R+该表示进程在前台运行        |
  | **l(**小写L)                        | 进程是多线程的，Sl表示进程是以线程方式运行(与程序)    |

- ## top命令详解

  ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240225141205130.png)q

- ##    案例

  - ### 过滤出crond进程信息 🌟🌟🌟🌟

    - ```sh
      ps -ef |grep crond
      ps -aux |grep crond
      ```

      > 过滤的结果可以通过grep -v grep 排除下grep命令自己(进程)
      >
      > ps -ef |grep crond |grep -v grep
      >
      > 后面还可以与wc配合使用统计进程数量。
      >
      > ps -ef |grep crond |grep -v grep |wc -l
      >
      > 根据过滤结果，随时调整过滤的命令条件。
      >
      > ps -ef |grep '/usr/sbin/sshd'

    - ### 按照树形结构查看进程信息🌟🌟🌟🌟

      - ```sh
        pstree 
        pstree -p #显示树形结构并输出pid.
        ps auxf #也可以展示部分所属关系，没有pstree直观
        ```

    - ### 根据要求,只显示某些内容🌟🌟🌟🌟

      - ```sh
        #通过awk取列
        ps aux | awk  '{print $1}'
        ps aux | awk  '{print $2}'
        ps aux | awk  '{print $3}'
        ps aux | awk  '{print $1,$3}'  #第1列和第3列
        #ps命令的选项,输出指定的内容
        ps axo user,%cpu,stat
        ps axo user,%cpu,stat,cmd	
        ```

    - ### 不显示标题

      - ```sh
        #awk写法 排除第1行,从第2行开始
        ps aux |awk 'NR>1{print $1,$3}'
        awk '{print 列}'
        awk '条件{print 列}'
        awk 'NR > = 1{print 列}'
        NR>1 行号大于1
        NR>=2 行号大于等于2 
        #ps不输出每一列的标题.
        ps -no-heading axo user,%cpu,stat
        ```

    - ### 取出某一个服务(crond)的进程信息(pid,%cpu,%mem,command)

      - ```sh
        ps aux |grep  'crond' |awk '{print $2}'
        ps aux |grep  'crond' |awk '{print $2,$3,$4,$11}'
        完全使用ps命令过滤出来
        ps -no-heading  -o pid,%cpu,%mem,command  -C crond
        --no-hea	ding 不显示标题
        -C 过滤 注意不要加上ax.
        -o输出指定列
        
        #awk输出最后列
        [root@oldboy-king tools]# echo 1 a b lidao 996 |awk '{print $NF}'
        996
        ```

    - ### 取出所有进程中的内存使用率最高的前5

      - ```sh
        #使用sort+ps
        ps aux |sort -rnk4
        ps -no-heading aux |sort -rnk4 |head -5 
        #只用ps命令方法
        ps aux   - sort=%mem |head -5
        默认是升序排序，指标前面加上-减号表示降序排序。
        ```

    - ### top基础使用与快捷键

      - ```sh
        #基础必会用法
        q 退出
        默认3秒刷新1次, 空格立刻刷新.
        P 默认按照CPU使用率排序
        M 按照内存使用率排序
        #进阶用法: 
         top输入z进入颜色模式 按 x 标记出当前是按照哪列排序.
         shift + > 向右
         shift + < 向左
        #top命令升级版，支持鼠标操作
        htop
        ```

    - ### 非交互模式

      - ```sh
        top |awk 'NR = 2'
        top  -bn1 |awk 'NR = 2'
        -b 非交互模式
        -n 只输出n次结果.
        ```

- ## 后台管理

  - 前台(前台运行): 需要连接后进行运行或操作,连接断开这个命令,操作就自动结束.

  - 后台(后台运行): 让软件进入系统的后台,持续运行,一般情况下连接断开了也不会影响软件运行

  - | 软件后台运行方法                           | 说明                                          | 应用场景                                         |
    | ------------------------------------------ | --------------------------------------------- | ------------------------------------------------ |
    | 1️⃣ 命令 &                                   | 常用的后台运行方法                            | 大部分时候使用这个即可                           |
    | 2️⃣nohup 命令 &                              | 与第1个类似,会记录输出到文件中默认叫nohup.out | 如果想记录输出可以用这个方法                     |
    | 2️⃣ 先运行命令,然后按下ctrl + z(后台挂起),bg | 软件进入后台运行                              | 顽固软件ctrl +c 无法结束,可以通过这个方法结束它. |
    | 3️⃣ screen命令                               | 通过软件创建空间,让命令在这个空间运行         | 稳定性比1️⃣ :four:                                 |

- ## &方法⭐️⭐️⭐️⭐️⭐

  - ```sh
    案例01 让sleep 999命令后台运行
    sleep 999 &
    [1] 1728
    [root@oldboy83-prod ~]# ps aux |grep 1728  
    root       1728  0.0  0.0 108052   356 pts/0   S    09:02   0:00 sleep 999
    root       1730  0.0  0.0 112824   976 pts/0   R+   09:02   0:00 grep -color=auto 
    1728
    ```

  - > [1] 1728
    >
    > 1表示 手动进入到后台运行的第1个进程。
    >
    > 1728表示进程pid
    >
    > jobs可以查看手动进入后台的进程

- ## nohup 命令 &

  - ```sh
    案例02 让ping baidu.com命令后台运行并记录输出
    nohup ping -c20 baidu.com &
    tail -f nohup.out
    ping -c 表示次数ping多少次
    ```

  - > 温馨提示 :如果想输出到其他文件
    >
    > nohup 命令 >新的文件 &即可
    >
    > nohup ping baidu.com >lidao-new.txt &

- ## ctrl +z

  - 这个快捷键不是撤销，这个快捷键在Linux下面表示让当前运行的命令或服务进入 后台挂起 ，如果转为后台运行需要在输入bg,如果是误触ctrl+z,可以通过fg让进程、命令回到前台。一般较少使用。

- ## screen

  - 一般使用&，nohub方法进入后台，一般不稳定这时候可以通过screen命令较为稳定的后台运行一些指令。

    简易原理：创建screen空间，screen命令维持，在里面运行的命令只要空间在，里面的命令就不会断（后台运行）。 

  - ```sh
    #1. 安装screen
    yum install -y screen 
    #2. 运行screen 
    screen
    进入screen虚拟窗口
    #3. 执行命令
    输入命令 ping baidu.com 
    #4. 退出screen窗口
    退出窗口(异常推荐,正常退出)
    ctrl + a 然后 d
    #5. 查看screen窗口
    查看
    screen -ls
    #6. 恢复
    screen -r 
    #彻底结束
    ctrl + d
    ```

- ## 杀手三剑客

  - 3个用于结束进程的命令

    | 命令     | 说明                                              |
    | -------- | ------------------------------------------------- |
    | **kill** | **kill +** **进程**pid **进行结束进程**,**常用**. |
    | pkill    | pkill + 进程名字, 取你狗命(你和狗),模糊查找.      |
    | killall  | killall + 进程名字,精确                           |

  - kill 信号

    - kill   pid 默认发送结束信号
    - kill -9 pid 发送强制结束信号.别用kill -9 结束数据库

- ## 负载(衡量系统繁忙程度指标.)

  - ### 概述

    - > 负载 load average 平均负载: 最近1分钟 5分钟 15分钟系统平均负载.
      >
      > 数值越接近cpu核心总数,系统的负载越高 .
      >
      > 建议负载达到cpu核心总数的70-80%。

    - > ==负载原理==:
      >
      > 那到底如何理解平均负载:**平均负载是指单位时间内，系统处于可运行状态****(R,S)**  **和不可中断状态** **(D)**的平均进程**
      >
      > **数，也就是平均活跃进程数**
      >
      > 负载是衡量正在运行的进程的平均数(可以中断进程和不可中断进程).
      >
      > 系统负载显示出什么信息:
      >
      > 负载主要衡量的是可运行状态(R,S 占用CPU)和不可中断 (io)

  - ### 负载高？	⭐️⭐️⭐️⭐️⭐

    - 排查流程
      - 1️⃣通过监控软件发现系统负载高(w,lscpu查看）.
      - 2️⃣判断是cpu还是io导致的负载高.
        - cpu高:top中的 us(user 用户占用cpu) sy(system 系统占用cpu)
        - io高: top中的 wa(iowait) 磁盘io导致的负载高
      - :three:
        - 🅰如果是cpu导致的,排查出哪个进程导致的ps aux过滤出占用cpu较高的进程。
        - 🅱如果是io导致的,排查初级哪个进程导致的，通过iotop -o命令排查。
      - 4️⃣未完待续.(具体分析这个进程有啥问题,第2阶段再说)
    - 图解
    - ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240225190055785.png)



# 系统管理体系之服务管理

1. ### systemctl服务管理

   - 开机自启动
   - 管理正在运行的服务

2. 检查sshd远程连接服务状态

   ```sh
   systemctl status sshd
   systemctl status 单个或多个服务名
   ```

3. 如何设置开启

   ```sh
   开机自启动
   systemctl enable sshd
   当前运行
   systemctl start sshd  #或者使用restart表示重启.
   ```

4. 关闭防火墙firewall

   ```sh
   #开机不会自动启
   systemctl disable firewalld.service
   #关闭正在运行的服务
   systemctl stop firewalld.service
   #服务永久关闭了
   systemctl status firewalld.service
   ```

5. 指令小结

   | systemctl          | 命令                        |
   | ------------------ | --------------------------- |
   | ✅开机自启动        | systemctl enable sshd       |
   |                    | systemctl disable firewalld |
   | ✅服务开启关闭重启  | systemctl start sshd        |
   |                    | systemctl stop sshd         |
   |                    | systemctl restart sshd      |
   | ✅查看服务状态      | systemctl status 服务名字   |
   | 服务运行情况       | systemctl list-units        |
   | 服务开机自启动情况 | systemctl list-unit-files   |

   - 服务无法使用systemctl管理实现，这时候怎么办？

     这时候我们可以使用/etc/rc.local文件。⚠️第1次使用需要授予执行权限 	chmod +x /etc/rc.d/rc.local

     然后把服务启动命令写入到/etc/rc.local 中即可。

     后面我们可以手动书写systemctl配置或脚本

   ## Linux 运行级别

   - ### ⭐️⭐️⭐️⭐️⭐

     | 运行级别 | 含义(c7)        | c6                               |
     | -------- | --------------- | -------------------------------- |
     | 0        | 关机            | 关机                             |
     | 1        | 救援模式 secure | 单用户模式,找回root密码          |
     | 2        | 多用户模式      | 无网络多用户模式                 |
     | 3        | 多用户模式      | 命令行模式,文本模式,工作默认模式 |
     | 4        | 多用户模式      | 未使用,待开发待使用。            |
     | 5        | 图形化界面模式  | 图形化界面模式                   |
     | 6        | 重启            | 重启                             |

   - ### 修改与查看

     - ```sh
       #查看当前系统运行级别
       systemctl get-default
       #修改运行级别（未来生产中不修改）
       systemctl set-default graphical.target #multi-user.target
       ```

   - ### Linux 启动流程⭐️⭐️⭐️⭐️⭐

     - ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240226003125063.png)
     - ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240226003205832.png)

6. ## root忘记密码如何解决

   1. 重启Linux
   2. 进入grub菜单（先不要继续）选择第1个（目前使用中的Linux内核），按 e ，编辑内核配置。
   3. 找到Linux16的行，修改这一行的内容 ro 改为 rw ，按 END 键到这一行的最后，输入 init=/bin/bash
   4. 修改完成，执行ctrl+x启动系统，进入救援模式（此时无法远程连接）。
   5. 通过vi/vim编辑/etc/passwd文件，去掉root的x标记（没有密码了），重启Linux.
   6. 本地登录Linux设置个密码即可

 

# 磁盘管理

![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240226131159134.png)

- ## 概述

  - 内存: 临时存放,断电丢失
  - 磁盘: 永久保存

- ## 分类

  - | 运行方式与原理 | 详细信息                                                     |
    | -------------- | ------------------------------------------------------------ |
    | 机械硬盘(HDD)  | 电机带动磁盘高速旋转,读取数据.速度可以达到5400,7200 rpm(每分钟多少转）（家用） |
    | 固态硬盘（SSD) | 集成电路与芯片,存储芯片.                                     |

- ## 磁盘接口

  - 磁盘接口:类似于水壶的壶嘴,磁盘的读写速度. 不同类型的磁盘接口有不同的读写速度.

  - | 接口分类 | 说明                                                      |
    | -------- | --------------------------------------------------------- |
    | **sata** | 一般家用,一般用于机械硬盘,也有固态硬盘,容量大，价格较低 . |
    | SAS      | 给企业环境使用,一般用于机械硬盘,也有固态硬盘              |
    | PCI-E    | 企业级使用,固态硬盘用.                                    |
    | U.2      | 企业级固态硬盘使用。PCI-E类似。                           |

- ## **企业级环境磁盘选型** ⭐️⭐️⭐️⭐️⭐

  - | 磁盘选型            | 应用建议                         |
    | ------------------- | -------------------------------- |
    | 一般情况下,数据备份 | SATA硬盘,10k rpm 4tb,8tb存放备份 |
    | 网站服务器使用      | SAS接口 15k rpm 300G 600G 900G   |
    | 高并发网站服务器    | 可以选择固态硬盘PCI-E,SAS,SATA   |

    ​	此建议基于物理服务器，如果是公有云，一般不用考虑过多

    > rpm是 round per minute 每分钟多少转的意思.

- ##  RAID⭐️⭐️⭐️⭐️⭐️

  - ### 概述

    - 在使用物理服务器的时候,多块硬盘,这些硬盘需要通过raid卡(设备),统一进行管理.
    - 大部分需要做raid后才能安装系统,部署服务.
    - raid 磁盘冗余阵列,管理磁盘方式.

  - ### 特点

    > 根据用户所设置的Raid级别可以获取如下一个或多个特点：
    >
    > 可以获取更高的容量.
    >
    > 可以获取更高的性能.
    >
    > 可以获取更高的冗余(安全).

  - ## riad级别⭐️⭐️⭐️⭐️⭐

    - ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240226162224966.png)

- ## 磁盘分区

  - MBR: 每一块硬盘上存放磁盘引导程序，引导程序在磁盘开头部分，用于引导系统启动。我们一般不用太关注，我们安装系统的时候自动安装。
  - 位置:磁盘分区表 磁盘的开始部分:0磁头,0磁道,1扇区(512字节)
  - 这512字节存放了
    - 引导程序446字节(MBR)
    - 磁盘分区表(64字节) 4个分区表
    - 结束标记 55AA，2字节
  - ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240226193254396.png)
  - 分区表64字节,每个分区占用16字节,最多只有4个分区
    - 这4个分区叫做主分区
      - 如果只划分1分区使用所有空间，将无法继续划分分区
      - 如果划分了4个分区，但是磁盘空间还有剩余，剩余空间将无法继续使用。
    - 扩展分区是用于解决主分区数量主分区只能有4个问题,扩展分区无法直接使用,需要在扩展分区下面创建逻辑分区,存放数据
    - 逻辑分区在扩展分区中,用于存放数据.
  - 主分区-扩展分区-逻辑分区关系
    - ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240226193437491.png)

- ## 磁盘及分区命名

  - 磁盘文件或分区文件放在/dev/下面

  - 命名方式如下

    - ```sh
      #磁盘接口:
         sas/sata/scsi接口的硬盘，硬盘名字是以sd开头
         虚拟机（kvm)/公有云:     硬盘名字是以vd开头
      #第几块硬盘：通过字母表示从字母a开始一次类推。
      /dev/sda
      #第1块硬盘(SAS)接口
      /dev/sda
      ```

    - 分区命名

      - > 分区命名是根据分区类型进行命名的。
        >
        > 如果是主分区或者扩展分区则分区号从1-4范围。
        >
        > 如果是逻辑分区，逻辑分区的分区号从5开始。

        ```sh
        案例01 硬盘及分区命名
        第2块SATA硬盘的第1个主分区   /dev/sdb1      
        第3块SAS硬盘的第2个逻辑分区   /dev/sdc6
        第5块公有云的云盘的第3个主分区 /dev/vde3
        ```

  - ## 实操

    - ```sh
      [root@oldboy-king-v2 ~]# fdisk -l |grep '/dev/sd'
      磁盘 /dev/sda：21.5 GB, 21474836480 字节，41943040 个扇区
      /dev/sda1   *        2048 2099199 1048576 83 Linux
      /dev/sda2         2099200 41943039 19921920   8e Linux LVM
      磁盘 /dev/sdb：106 MB, 106954752 字节，208896 个扇区
      磁盘 /dev/sdc：106 MB, 106954752 字节，208896 个扇区
      磁盘 /dev/sdd：3221.2 GB, 3221225472000 字节，6291456000 个扇区
      
      案例02 sdb硬盘创建20MB的分区
      fdisk /dev/sdb
      #1 操作硬盘
      fdisk /dev/sdb
      #2. 对硬盘分区进行增删改查
      p print 输出磁盘分区信息
      n new   创建分区
      d delete 删除分区
      w write 保存并退出
      q quit 退出不保存
      #3. 创建20MB分区
      命令(输入 m 获取帮助)：n  #创建分区
      Partition type:        #提示选择 类型
         p   primary (0 primary, 0 extended, 4 free)
         e   extended
      Select (default p): 回车即可  #输入p或回车默认使用主分区
      Using default response p
      分区号 (1-4，默认 1)：回车即可  #分区号回车使用默认的1号
      起始 扇区 (2048-208895，默认为 2048)：回车即可 #回车,使用默认的起点
      将使用默认值 2048
      Last 扇区, +扇区 or +size{K,M,G} (2048-208895，默认为 208895)：+20M      #+20M分区20MB    
      分区 1 已设置为 Linux 类型，大小设为 20 MiB
      #4. 通过p查看
      命令(输入 m 获取帮助)：p
      磁盘 /dev/sdb：1073 MB, 1073741824 字节，2097152 个扇区
      Units = 扇区 of 1 * 512 = 512 bytes
      扇区大小(逻辑/物理)：512 字节 / 512 字节
      I/O 大小(最小/最佳)：512 字节 / 512 字节
      
      ```

    - ### 格式化（创建文件系统）⭐️⭐️⭐️⭐️⭐️

      - 创建 make 文件系统 filesystem,表示给磁盘分区进行装修，给磁盘分区创建规则，一定量的inode，block。

      - mkfs（make filesystem) 创建文件系统(格式化)

        ```sh
        mkfs 磁盘或分区
        mkfs.xfs /dev/sdb1
        xfs是文件系统类型，CentOS 7默认的文件系统类型。
        mkfs.ext4 文件系统类型，用于CentOS 6.x 或公有云使用。
        ```

    - ### 挂载

      - Linux中的设备，需要通过挂载命令，给设备指定入口（已经存在的空目录）,否则将无法使用.
      - 通过mount命令指定 设备 ，指定 入口(目录) mount 设备 目录
      - 入口: 挂载点,一般是个空目录就行. /mnt linux临时挂载点

    ```sh
    #临时挂载（重启Linux系统后挂载失效）
    mount /dev/sdb1 /mnt/
    [root@oldboy-lnb-king-v3 ~]# df -h
    文件系统                                 容量 已用 可用 已用% 挂载点
    devtmpfs                                 979M     0 979M    0% /dev
    tmpfs                                     991M     0 991M    0% /dev/shm
    tmpfs                                     991M  9.6M 981M    1% /run
    tmpfs                                     991M     0 991M    0% /sys/fs/cgroup
    /dev/mapper/centos_oldboy--king--v2-root   47G  2.6G   45G    6% /
    /dev/sda1                               1014M 138M 877M   14% /boot
    tmpfs                                     199M     0 199M    0% /run/user/0
    /dev/sdb1                               1020M   33M 988M    4% /mnt
    [root@oldboy-lnb-king-v3 ~]# #给/dev/sdb1 设置入口，入口叫/mnt/
    [root@oldboy-lnb-king-v3 ~]# mount /dev/sdb1 /mnt/
    [root@oldboy-lnb-king-v3 ~]# df -h |grep mnt
    /dev/sdb1    
    ```

    - ### 卸载

      ```sh
      umount /mnt
      umount + 挂载点，表示卸载。
      ```

  - ## 永久挂载⭐️⭐️⭐️⭐️⭐

    - 方案1️⃣使用rc.local ,把挂载命令 mount /dev/sdb1 /data/ 写入到/etc/rc.local,注意命令最好写为绝对路

      > rc.local 开机配置文件

    - 方案2️⃣专业的开机自动挂载的配置文件/etc/fstab ,根据配置文件的要求把mount命令改为配置文件形式即可。

    - ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240226202102036.png)
  
  - ## mbr vs gpt
  
    - | 分区表 | 特点                                                         | 对应命令     |
      | ------ | ------------------------------------------------------------ | ------------ |
      | mbr    | 支持2tb以内的硬盘,大于2tb则只识别2tb. 区别主分区,扩展分区,逻辑分区 | fdisk/parted |
      | gpt    | 支持大容量硬盘,主分区无限使用(100多个).                      | gdisk/parted |
  
  - ## 创建swap
  
    - swap交换分区:内存不足的时候临时充当内存,swap占用的磁盘空间.
  
    - 所以未来应用建议:如果内存充足并且服务对性能要求较高,可以关闭swap
  
    - ```sh
      #案例05 服务器运行java程序,大量占用内存,以至于开始占用swap如何解决?
      - 一步保证网站正常,增加swap空间.
      - 联合开发一起排查.
      增加1g的swap.
      1.创建指定大小的文件1g的文件.
      2.把文件转换为swap.
      3.激活这个swap,把它加入到linux中.
      4.记得配置永久挂载.
      ```
  
    - ```sh
      #1.创建指定大小的文件1g的文件.
      dd if=/dev/zero of=/tmp/1g  bs=1M count=1000
      if === input file 数据从哪里来,输入文件,一般使用/dev/zero,不断输出空字符.
      of === ouput file 创建的文件,存放数据,输出文件
      bs === block size 每次读取多少,一般1MB大小.
      count === 读取次数
      2.把文件转换为swap(格式化).
      mkswap /tmp/1g
      -----------------------
      root@oldboy-king-v2 ~]# file /tmp/1g 
      /tmp/1g: data           #刚刚创建的文件data普通数据文件
      [root@oldboy-king-v2 ~]# mkswap /tmp/1g 
      正在设置交换空间版本 1，大小 = 1023996 KiB
      无标签，UUID=0c072a5f-5ec2-4590-acd3-cae1e1926029
      [root@oldboy-king-v2 ~]# file /tmp/1g       #成为了swap 文件
      /tmp/1g: Linux/i386 swap file (new style), version 1 (4K pages), size 255999 pages, no label, 
      UUID=0c072a5f-5ec2-4590-acd3-cae1e1926029
      --------------------------
      3.激活这个swap,把它加入到linux中.
      [root@oldboy-king-v2 ~]# free -h
                   total       used       free     shared buff/cache   available
      Mem:           1.9G       201M       596M        9.6M        1.2G        1.6G
      Swap:          2.0G         0B        2.0G
      chmod 600 /tmp/1g
      swapon /tmp/1g
      free -h
                   total       used       free     shared buff/cache   available
      Mem:           1.9G       202M       595M        9.6M        1.2G        1.6G
      Swap:          3.0G         0B        3.0G
      4.记得配置永久挂载.
      方法01 : swapon /tmp/1g写入到rc.local 
      方法02: 写入/etc/fstab
      /tmp/1g       swap     swap   defaults        0 0
      ```
  
  - ## 系统管理磁盘管理之故障案例
  
    - | 故障分类         | 现象                                                  | 排查                                            |
      | ---------------- | ----------------------------------------------------- | ----------------------------------------------- |
      | block            | df -h磁盘空间不足                                     | df -h,du -sh一层一层找,直到找出对应的文件或目录 |
      | inode            | df -h磁盘空间有剩余,创建文件,操作服务提示磁盘空间不足 | df -h,df -i,找出系统中的大目录                  |
      | block 文件未彻底 | df -h查看磁盘空间不足,du -sh 查看磁盘空间还有         | loof \|grep delete,找出进程或服务               |
  
      

# 特殊符号

- ## 引号系列⭐⭐⭐⭐⭐

- | 引号     | 含义                                                         |
  | -------- | ------------------------------------------------------------ |
  | 单引号   | 所见即所得,单引号的内容会原封不动输出                        |
  | 双引号   | 和单引号类似,对双引号里面的特殊符号会进行解析,对于{ }花括号(通配符)没有解析 |
  | 不加引号 | 和双引号类似,额外支持通配符(匹配文件)*.log {01..10}          |
  | 反引号   | 优先执行,先执行反引号里的命令                                |

- ```sh
  #单引号
  echo  '`hostname` lidao996   $(whoami) $UID {1..5} 
  '
  #双引号
  echo  "`hostname` lidao996   $(whoami)  $UID {1..5} 
  "
  #不加引号
  echo  `hostname` lidao996   $(whoami)  $UID {1..5}
  ```

- > hostname 表示执行hostname命令
  >
  > $(whoami) 表示执行whoami命令
  >
  > $UID 表示取出当前用户的uid
  >
  > {1..5} 输出1 2 3 4 5

- ## 重定向符

- ### 概述

  - 改变输出的方向

  ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240227193939972.png)

- ## 重定向符号

  - | 重定向符号             | 含义                                                  | 应用场景                                  |
    | ---------------------- | ----------------------------------------------------- | ----------------------------------------- |
    | > 或 1>                | 标准输出重定向: 先清空文件,然后写入.                  | 大部分情况下先清空的时候可以使用 创建文件 |
    | >> 或 1>>              | 标准输出追加重定向: 直接写入到文件末尾                | 修改文件配置表示追加的时候                |
    | 2>                     | 标准**错误**输出重定向: 先清空文件,然后写入错误信息   | 较少单独用,一般用于获取所有输出.          |
    | 2>>                    | 标准**错误追加**输出重定向: 直接把错误写入到文件末尾. | 较少单独用,一般用于获取所有输出.          |
    | 命令 >>oldboy.log 2>&1 | 无论对错都把结果写入到文件中.                         | 比较常用,定时任务,脚本中常用              |
    | 命令 &>>oldboy.log     | 无论对错把结果都写入文件                              | 同上                                      |
    | < 或0<                 | 标准输入重定向                                        | 很少用,搭配某几个命令用xargs,tr           |
    | << 或 0<<              | 标准输入追加重定向                                    | 与cat搭配使用表示向文件内写入多行内容     |

- ```sh
  [root@oldboy-aliyun-servers ~Վʠ eco aaaa   
  ՎҴlidao.txt 
  -bash: eco: command not found
  [root@oldboy-aliyun-servers ~Վʠ cat lidao.txt 
  lidao
  lidao
  [root@oldboy-aliyun-servers ~Վʠ eco aaaa   
  2ՎҴlidao.txt 
  [root@oldboy-aliyun-servers ~Վʠ 
  [root@oldboy-aliyun-servers ~Վʠ 
  [root@oldboy-aliyun-servers ~Վʠ cat lidao.txt 
  lidao
  lidao
  -bash: eco: command not found
  
  #最容易理解的方法
  echo   oldboy   ՎҴ oldboy.log    2ՎҴoldboy.log
  #日常常用的方法之一
  echo   oldboy   >oldboy.log     2>&1
  2>&1 表示 把2错误输出写入到标准输出中(1) （错误输出合并到标
  准输出中，都追加到oldboy.log中）
  #最简写法
  echo   oldboy   &ՎҴoldboy.log
  
  xargs -n3 <num.txt 
  1 2 3
  4 5 6
  7 8 9
  10
  
  
  <<用于与cat命令实现写入多行内容.
  格式:
  cat >文件<< 结束标记
  结束标记
  结束标记两边不要有多余符号
  一般都是事先写好,然后粘贴到命令行执行.
  cat >oldboy.txtՎӒEOF
  I 
  love 
  linux
  EOF
  EOF End of File文件结束的缩写.
  #另外的一种cat的格式
  cat <<EOF   >oldboy.txt 
  I 
  love 
  linux
  EOF
  EOF End Of File文件结束
  ```

- ## 通配符

  - | 符号     | 含义                         |
    | -------- | ---------------------------- |
    | *星号    | 所有 , *.txt *.log '*ip*'    |
    | {}花括号 | 输出序列,与echo,touch,mkdir. |
    | []       | 参考正则中含义即可           |
    | [!] [^]  | 取反                         |
    | ?        | ? 任意一个字符               |

    ```sh
    #基本用法
    echo {aՎʡz}
    echo {1Վʡ10}
    #输出等宽的数字序列 01 02 03 10   001 002 ՎՎʢ 100
    echo {01Վʡ10}
    echo {01Վʡ100}
    #输出无规律
    [root@oldboy-85-vip-king-v2 ~]# echo 
    {lidao,oldboy,zhangsan}
    lidao oldboy zhangsan
    [root@oldboy-85-vip-king-v2 ~]# echo oldboy-
    {lidao,oldboy,zhangsan}
    oldboy-lidao oldboy-oldboy oldboy-zhangsan
    # seq 输出1 3 5 7 9 
    [root@oldboy-85-vip-king-v2 ~]# seq 1 3 10 
    1	
    4
    7
    10
    # 使用{}实现:了解
    [root@oldboy-85-vip-king-v2 ~]# echo {1..10..2}
    1 3 5 7 9
    [root@oldboy-85-vip-king-v2 ~]# echo {a..z..2}
    a c e g i k m o q s u w y
    #小技巧: 备份某一个文件
     [root@oldboy-85-vip-king-v2 ~]# cp 
    oldboy.txt{,.bak}
    [root@oldboy-85-vip-king-v2 ~]# ll oldboy.txt* 
    -rw-rՎʔrՎʔ. 1 root root 23 12月 23 10:44 oldboy.txt
    -rw-rՎʔrՎʔ. 1 root root 23 12月 23 11:26 
    oldboy.txt.bak
    [root@oldboy-85-vip-king-v2 ~]# echo 
    oldboy.txt{,.bak}
    oldboy.txt oldboy.txt.bak
    [root@oldboy-85-vip-king-v2 ~]# echo A{,B}
    A AB
    [root@oldboy-85-vip-king-v2 ~]# 
    [root@oldboy-85-vip-king-v2 ~]# echo A{C,B}
    AC AB
    
    找出/bin目录下面命令,命令仅有2个字符组成.
    ls -l /bin/??
    
    ```

  - # 正则表达式

    - ## 概述

      - 用于给Linux三剑客,程序语言使用的.
      - 使用正则表达式对 字符进行过滤 . 使用三剑客实现日志的过滤.
      - 正则表达式本质是一些符号 ^ $  ^. * .* [] [^] | () + {} ? . 

  - ## 正则与通配符区别

    - | 区别   | 用途                     | 支持命令不同          |
      | ------ | ------------------------ | --------------------- |
      | 正则   | 匹配文件内容( 匹配字符 ) | 三剑客支持,开发语言   |
      | 通配符 | 匹配文件名               | linux大部分命令都支持 |

  - ## 分类

    - | 分类     | 符号                 |
      | -------- | -------------------- |
      | 基础正则 | ^ $  $ . * .* [] [^] |
      | 扩展正则 | \| \+ () {} ?        |

  - ## 基础正则

    - ### ^以....开头的行

      - ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240228153918734.png)

    - ### $以...结尾

      - ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240228154128227.png)

      - > cat -A 显示出文件中的特殊隐藏符号.

    - ### ^$ 空行,这行没有任何字符

      - ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240228154408864.png)

      - ![排除空行](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240228154606744.png)

      - > 排除/etc/ssh/sshd_config文件中的空行,然后排除以#号开头的行(可以使用管道)
        >
        > grep -v '^$' /etc/ssh/sshd_config |grep -v '^#'

    - ### . 任意一个字符,不匹配空行

      - ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240228155046207.png)

      - > grep -o选项,显示正则匹配到了什么? 显示执行过程.

        ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240228155134252.png)

    - ### \撬棍 转义字符 脱掉马甲打回原形,去掉特殊符号的含义

      - ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240228155301321.png)

    - ### * 前一个字符连续出现0次或0次以上

      - ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240228160057311.png)

    - ### .* 所有,任何字符

      ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240228160733854.png)

    - > 正则表示**连续出现**的时候或者表示**所有**的时候,正则体现出贪婪性,尽可能多的匹配.
      >
      > 未来我们根据实际的需求使用贪婪性即可.

    - ### [ ] [abc]  表示匹配任意一个字符,a或b或c,中括号相当于一个字符

      - > () 小括号
        >
        > [] 中括号
        >
        > {} 大括号 花括号

        ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240228161549639.png)

        ![image-20240228161603873](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240228161603873.png)

        ```sh
        #匹配数字
        grep '[0-9]' re.txt
        #匹配小写字母
        	[a-z]
        #匹配大写字母
        	[A-Z]
        #匹配大小写字母
        	[a-zA-Z]
        	[a-Z] #如果这个用不了使用上面完成形式
        ```

      - ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240228161859583.png)

      - ```sh
        #匹配大小写字母+数字
        grep '[a-zA-Z0-9]' re.txt 
        grep '[a-Z0-9]' re.txt 
        grep '[0-Z]' re.txt
        ```

    - ### [^] [ ^abc ] 表示匹配任意一个字符,排除abc

      - ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240228162118088.png)

  - | 基础正则 | 含义                       |
    | -------- | -------------------------- |
    | ^        | 以xxx开头                  |
    | $        | 以xxx结尾                  |
    | ^$       | 空行                       |
    | .        | 任意字符                   |
    | \        | 转义字符,撬棍              |
    | *        | 前一个字符出现0次或以上    |
    | .*       | 所有                       |
    | []       | [abc] a或者b或者c          |
    | [^]      | [^abc] 匹配除abc之外的内容 |

- ## 扩展正则

  - +前一个字符连续出现1次或者一次以上
  
  - | 或者
  
  - ()表示整体,用于后向引用
    - ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240228173848979.png)
    
    - {} a{n,m} 前一个字符连续出现至少n次最多m次
      - ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240228173941502.png)
      - ? 前一个字符 出现 0次或1次
    
    - ## 三剑客之sed
    
      - | 选项   | 说明                                     |
        | ------ | ---------------------------------------- |
        | -n     | 取消默认输出                             |
        | -r     | sed支持扩展正则                          |
        | -i     | 修改文件内容,需放在最后                  |
        | -i.bak | 先进行备份,然后修改文件内容,需要放在最后 |
    
    - ## sed增删改查 :star:
    
      - ```sh
        #案例01: 取出文件的第3行
        sed -n '3p' /etc/passwd
        
        #案例02: 取出/etc/passwd的第2行到第5行
        sed -n '2,5p' /etc/passwd  ,改为;就是只显示2行和5行
        
        #案例03: 过滤出/etc/passwd中包含root的行
        sed -n '/root/p' /etc/passwd
        
        # 把sed.txt文件中lidao替换为oldboy
        sed 's#lidao#oldboy#g' sed.txt
        ```
    
      - ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240312165622130.png)
    
    - ## 三剑客之awk
    
      - ### awk概述
    
        - | 四剑客     | 特点                                  | 擅长                    |
          | ---------- | ------------------------------------- | ----------------------- |
          | find       | 查找文件                              | 查找文件,与其他命令配合 |
          | grep/egrep | 过滤                                  | 过滤速度最快            |
          | sed        | 过滤,取行,替换,删除                   | 替换,修改文件内容,取行  |
          | awk        | 过滤,取行,取列,统计计算,判断,循环 ... | 取列,取行,统计计算      |
    
        - awk是一个语言,叫做单行脚本
    
        - 格式
    
          - ```sh
            取出/etc/passwd中的第1行的第1列,第3列和最后一列
            awk   -F:   'NR==1{print $1,$3,$NF}' /etc/passwd
            awk   选项   '条件{动作}'   /etc/passwd
            条件 找谁
            动作 干啥
            ```
    
        - ### 执行流程
    
          - ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240312191906918.png)
    
      - ### 取行
    
        - ```sh 
          #案例01 : 取出/etc/passwd的第1行
          awk  'NR==1{print $0}' /etc/passwd
          awk 'NR==1' passwd
          ```
    
        - > NR Number of Record 记录号,行号.
          >
          > == 表示等于
          >
          > {print $0} 输出整行内容 \$0表示当前行的内容. awk满足条件后默认的动作,输出这一行的内容.
          >
          > 上面仅取行,还可以简写为
          >
          > awk  'NR==1' /etc/passwd
    
        - ```sh
          #案例02: 取出第2行到第5行的内容
          awk 'NR>=2&&NR<=5' /etc/passwd
          ```
    
        - > \>= 表示大于等于
          >
          > && 表示并且
          >
          > || 表示或者
    
        - 
    
          ```sh
          #案例03: 过滤出/etc/passwd文件中包含root或nobody的行
          awk '/root|nobody/' /etc/passwd
          
          #案例04 : 从包含root的行到包含nobody的行
          awk '/root/,/nobody/' /etc/passwd
          ```
    
      - ### 取列
    
        -  ```SH
           #案例05: 使用awk取出ls -lh 的大小列和最后一列
            ls -lh /etc/hosts | awk '{print $5,$9}'
            ls -lh /etc/hosts | awk '{print $5,$NF}'
           ```
    
        - > awk中取列的时候说明:
          >
          > \$数字,表示取列,$1 第1列 $0表示这一行.
          >
          > $NF 最后一列
          >
          > NF Number of Field 每行有多少列
          >
          > $(NF-1) 取出倒数第2列,一般用于正向取发生变化或数字过大
          >
          >  
          >
          >  awk输出对齐:
          >
          > 使用column命令即可或者使用\t
          >
          > ```sh
          > ll -h |awk '{print $5,$9}'|column -t
          > ll -h |awk '{print $5"\t"$9}'
          > ```
    
        - ```sh
          #案例06: 取出/etc/passwd中的第1列,第3列和最后一列
          awk -F':'   '{print $1,$3,$NF}' /etc/passwd|column -t
          ```
    
        - > awk取列的时候,默认是通过空白字符进行分割的.
          >
          > 空白字符:空格,连续空格,tab键.
          >
          > 但是一些时候使用默认分隔符不够了,需要我们手动指定分隔符,通过-F选项指定.
          >
          > 未来我们想快速取出想要的内容,选择趁手工具(选好分隔符).
          >
          > 选择分隔符建议: 看你目标两边是啥.
    
        - ```sh
          #案例07: 指定复杂分隔符取出ip
          ip a s eth0 |awk 'NRՎҧ3'|awk '{print $2}'|awk -F'/' '{print $1}'
          遇到空格或/就切一刀,所以4个空格切4刀,ip是第6列
          ip a s eth0 | awk 'NR==3'|awk -F'[ /]' '{print $6}'
          其他分隔符取出
          ip a s eth0 |awk 'NR==3' |awk -F 'inet |/24'
          '{print $2}'
          ```
    
      - ### 取行与取列
    
        - ```sh
          #案例08: 取行+取列 取ip地址
          awk   选项   '条件{动作}'   /etc/passwd
          ip a s eth0 | awk -F'[ /]+'  'NR==3{print $3}'
          10.0.0.200
          
          #案例09: 取出/etc/passwd文件中第3列大于大于100的行,取出这行的第1列,第3列和最后一列
          awk -F':'  '$3>=100{print $1,$3,$NF}' /etc/passwd |column -t
          
          #案例10: 如果系统swap使用超过0则输出"异常系统开始占用swap"
          free |awk '/Swap/ && $3 >=0 {print "异常系统开始占用swap"}'
          
          #案例11: 过滤出/etc/passwd第4列的数字是以0或1开头的行,输出第1列,第3列,第4列
          awk -F':' '$4 ~ /^[01]/ {print $1,$3}' /etc/passw
          ```
      
          > 温馨提示 awk中 通过~可以实现对某一列进行过滤
          >
          > 某一列中含有xxxx内容
          >
          > ~ 表示包含的意思 $1 ~ /root/ 表示第1列中包含root
          >
          > !~ 表示不包含
      
      - ### awk统计与计算
      
        - 统计次数
      
          - ```sh
            awk  '{i=i+1} END{print i}' /etc/passwd
            ```
      
            > END{}内容会在awk读取完成文件的时候执行.
            >
            > END{}一般用于输出执行结果.
            >
            > i=i+1 ===i++

#  第一个必会服务-定时任务

- ## 服务使用流程

- | 服务使用流程`  | 说明                                                         |
  | -------------- | ------------------------------------------------------------ |
  | 部署           | 安装这个软件或者服务                                         |
  | 配置           | 如何使用这个服务通过配置文件,通过命令. 初级使用:能用就行. 提高:额外配置. |
  | 优化或注意事项 | 安全.......                                                  |
  | 排障           | 难点 1 通过错误提示解决问题,2 学会看日志 ,让服务出错误提示或者输出更加详细的错误提示(通过重定向) |
  | 其他           | 做好监控,做好备份,做好日志收集,统一认证                      |

  

- ## 部署定时任务

  - 定时任务软件包名字:cronie , 服务名字(进程)crond

  - ```sh
    rpm -qa cronie
    rpm -ql cronie
    ```

  - **crontab**  定时任务管理的命令

    - -e 编辑当前用户的定时任务
    - -l 查看当前用户的定时任务

  - 定时任务书写格式-时间

    - ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240313201523259.png)

    - > 每天早上8:30分 去学校(go to school)
      >
      > \#1.test01
      >
      > 30 08 * * * go to school
      >
      > 晚上12点上床睡觉(go to bed/sleep) dbj 
      >
      > \#2.test02
      >
      > \*  00 * * * go to bed #每天的半夜12点00-59 每分钟运行.
      >
      > 00 00 * * * go to bed #每天运行
      >
      > 问题:
      >
      > **表示整点的时候,未说明分钟的时候,我们要指定的分钟,一般是00.**
      >
      > **关于分钟位置上是否写*说明**
      >
      > **涉及到小时,天,周几的时候,分钟位置上记得写个数(00)**

    - ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240313201806504.png)

    - > 每天的上午7点到晚上11点 每二个小时运行CMD命令
      >
      > 00 07-23/2 * * * CMD
      >
      > 07 09 11 13 15 17 19 21 23
      >
      > 定时任务每天23点到第2天的7点运行.
      >
      > 00 23,00-07 * * *

    - **定时任务案例**

      - ```sh
        #1. 同步时间 by lidao996 at 20221111
        */2 * * * * /sbin/ntpdate ntp1.aliyun.com 
        >/dev/null  2>&1
        
        #2. 定时备份 /etc/ 目录 by lidao996 at xxxx 
        mkdir -p /backup/
        tar zcf /backup/etc-`date +%F_%w`.tar.gz /etc/
        专用脚本目录:
        mkdir -p /server/scripts/
        #书写脚本
        cat backup-etc.sh
        tar zcf /backup/etc-`date +%F_%w`.tar.gz /etc/
        
        sh backup-etc.sh
        
        * * * * * /bin/sh /server/scripts/backup-etc.sh 
        >/dev/null  2>&1
        ```

      - **脚本与变量**

        - > \#赋值 修改变量内容(创建)
          >
          > kui="欲练此功必先自宫,如不自宫也能成功"
          >
          > \#取值
          >
          > echo $kui
          >
          > 欲练此功必先自宫,如不自宫也能成功

      - **定时任务注意事项**

        - 1增加注释

        - 2尽量使用脚本

          - > 调试脚本的方法:
            >
            > **sh -x 或bash -x ,显示脚本执行过程.**
            >
            > **有+开头的表示脚本背后执行的过程.**
            >
            > **如果开头没有+,表示输出.**

      - **定时任务的文件**,**脚本使用绝对路径**

      - > 在定时任务运行命令或脚本的时候,只能识别到/bin或/usr/bin目录下面的命令.
        >
        > 只要不在这些目录下面的命令,就要使用绝对路径或者重新定义下PATH环境变量.

        - 可以通过2种方法解决

        - > **1**  在脚本文件的开头声明PATH环境变量
          >
          > ```sh
          > export PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin
          > ```
          >
          > **2**  脚本开头重新加载PATH变量
          >
          > ```SH
          > source /etc/profile
          > ```

        - **定时任务中执行的命令或脚本定向到空或追加到文件**

          - > \#定向到空
            >
            > \#1. 同步时间 by lidao996 at 20221111
            >
            > */2 * * * * /sbin/ntpdate ntp1.aliyun.com \>/dev/null  2>&1
            >
            > \#追加到文件同理

      - ### 定时任务直接书写%有特殊含义 (使用脚本则没有,也可用 \ )

    - ## 案例

      - ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240314000842417.png)

    - ### 定时系统巡检(定时输出系统基本信息)写入到/tmp/sys.log中

    - ### 发送邮件
    
      - > ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240314145616191.png)
        >
        > ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240314145637749.png)
        >
        > ![](C:\Users\lingpfeng\AppData\Roaming\Typora\typora-user-images\image-20240314145710856.png)
    

# 一些命令总结

- ## 查看端口

  在Linux和类Unix系统中，查看端口的状态和监听情况，可以使用多种命令。以下是一些常用的命令：

  1. **netstat**：
     `netstat` 是一个非常强大的网络工具，可以显示网络连接、路由表、接口统计等信息。要查看所有端口的状态，可以使用：
     
     ```bash
     netstat -tuln 
     ```
     - `-t` 表示 TCP
     - `-u` 表示 UDP
     - `-l` 表示仅显示监听状态的端口
     - `-n` 表示显示数字形式的地址和端口号
     
  2. **ss**：
     `ss` 是另一个实用的网络工具，用于查看套接字统计。它可以被视为 `netstat` 的现代替代品。要查看端口，可以使用：
     
     ```bash
     ss -tuln
     ss -ant
     ```
     - ss -ant` 命令的参数组合用于显示所有（`-a`）TCP（`-t`）和UDP（`-u`）的监听套接字（`-n`），而不解析服务名称（`-a`），这样可以更快地显示结果。
     
       具体来说，`ss -ant` 命令的参数解释如下：
     
       - `ss`: 是 "socket statistics" 的缩写，即套接字统计。
       - `-a`: 显示所有套接字，包括监听和非监听的。
       - `-n`: 不解析服务名称（例如，不将端口号转换为服务名称，如 HTTP 或 SSH）。
       - `-t`: 显示TCP套接字。
       - `-u`: 显示UDP套接字。
     
       在这个输出中，你可以看到每个监听套接字的状态（LISTEN），接收队列和发送队列的大小（Recv-Q 和 Send-Q），本地和外部的地址和端口，以及关联的进程信息（Process 列显示进程名称和进程ID）。
     
       这个命令对于快速检查系统上运行的服务和监听的端口非常有用，特别是在排查网络问题或确认服务状态时。由于 `ss` 命令比 `netstat` 更快，它在生产环境中被广泛使用。
     
  3. **lsof**：
     `lsof` 命令用于查看被进程打开的文件。由于在Unix中一切皆文件，网络连接也包括在内。要查看端口，可以使用：
     
     ```bash
     lsof -i -n | grep LISTEN
     ```
     - `-i` 表示显示网络连接
     - `-n` 表示避免对地址和端口进行解析
     
  4. **nmap**：
     `nmap` 主要用于网络发现和安全审计。它可以用来扫描端口。要检查本地机器的端口，可以使用：
     ```bash
     nmap -sT -O localhost
     ```
     - `-sT` 表示进行TCP连接扫描
     - `-O` 表示进行操作系统检测

  5. **fuser**：
     `fuser` 命令用于查找使用指定资源的进程。要查看特定端口的进程，可以使用：
     ```bash
     fuser -v -n tcp port_number
     ```
     - `port_number` 是你想要检查的端口号

  6. **iptables**：
     `iptables` 是一个配置Linux内核防火墙的命令行工具。要查看防火墙规则（包括端口），可以使用：
     ```bash
     iptables -L -n -v
     ```
     这将列出所有的iptables规则，包括允许和拒绝特定端口的规则。

  请注意，某些命令可能需要root权限才能查看所有信息。如果你不是以root用户运行，可以在命令前加上 `sudo` 来获取必要的权限。

  在使用这些命令时，请确保你有权限执行它们，并且了解它们可能对系统造成的影响。特别是在使用 `iptables` 进行规则修改时，错误的操作可能会导致网络连接问题。

  ```SH
  tr -cd 'a-z' < /dev/urandom|head -c10**
  ```

  该命令组合是在一个类Unix系统中使用的，用于从`/dev/urandom`设备文件中生成随机字符序列。下面是对命令各部分的解释：

  - `tr`：是“translate”或“squeeze”的缩写，用于删除或替换文件中的字符。在这个例子中，`tr`用于从输入中删除字符。
  - `-c`：这个选项用于压缩重复的字符，只保留一个。
  - `-d`：这个选项用于删除输入中的重复行。
  - `'a-z'`：这是`tr`命令的操作字符集，指定了`tr`操作的字符范围。在这个例子中，它表示所有的小写字母。
  - `< /dev/urandom`：这是输入重定向，意味着`/dev/urandom`文件的内容将作为输入传递给`tr`命令。`/dev/urandom`是一个特殊的文件，提供了一个强随机性的源，通常用于生成随机数或密钥。
  - `head -c10`：这是另一个命令，用于从输入中只取前10个字符。`head`命令默认输出文件的前10行，但在这里使用`-c`选项来指定输出的字符数。

  综合来看，这个命令组合的作用是从`/dev/urandom`生成的随机数据中，提取10个不重复的小写字母字符。这可以用于生成一些简单的随机字符串，例如用于测试或临时的密码。

  需要注意的是，虽然`/dev/urandom`提供的随机性对于大多数用途来说是足够的，但它生成的随机数并不适用于加密用途。对于需要高安全性的随机数生成，应使用专门的加密函数或工具。此外，生成的字符串长度较短，可能不满足某些安全策略对于密码长度的要求。在实际应用中，应根据具体需求选择适当的随机数生成方法和长度。

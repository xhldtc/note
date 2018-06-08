#nohup 

```bash
nohup command_line &
```
作用是将进程提交到后台运行，即使终端退出也不影响进程的运行

```bash
nohup command_line > output 2>&1 &
```

将stdout重定向到output文件中，并将stderr重定向到stdout中，其实也就是重定向到output文件中

#tailf

```bash
tailf filename
```
将文件的最后10行打印出来，会随着文件的增长不断打印添加的内容，非常适合log的跟踪

#ps

查看进程，常用组合就几个，其他选择查看man

```bash
ps aux
```
列出所有进程，包括无控制终端的进程，并显示进程所属的用户名

```bash
ps -ef
```
列出所有进程，包含父进程和子进程的关系、最近CPU使用、进程开始时间、终端名以及相关的命令语句

#lsof

是list open files的缩写

```
lsof -i:1234
```
可以查出哪个进程在占用1234这个端口


#ifconfig

mac下可用该命令组合其他命令获得本机ip地址，首先执行ifconfig,然后我们感兴趣的一段是这样的

```bash
en0: flags=8863<UP,BROADCAST,SMART,RUNNING,SIMPLEX,MULTICAST> mtu 1500
	ether f4:5c:89:8f:b7:a5
	inet6 fe80::f65c:89ff:fe8f:b7a5%en0 prefixlen 64 scopeid 0x4
	inet 192.168.21.121 netmask 0xfffffc00 broadcast 192.168.23.255
	nd6 options=1<PERFORMNUD>
	media: autoselect
	status: active
```
其中inet行就有本机的ip，然后执行如下命令就能截到ip了

```bash
ifconfig | grep 'inet.*netmask.*broadcast' | awk '{print $2}'
```

#kill

```bash
kill -9 pid
```
强制结束id为pid的进程

#ln

```bash
ln -s source target
```
创建软链接，source和target可为文件或目录，相当于Windows里的快捷方式

#which

```bash
which file
```
查找可执行文件在PATH里哪个路径下，只显示第一个搜索结果，加-a参数会列出所有切匹配的路径

PS:如果相同文件名的可执行文件在PATH里存在多个路径，PATH在查找的时候以顺序优先去匹配，配在越前面的路径优先级越高

#chmod

```bash
chmod u+x hello.sh
```
为当前用户添加脚本的可执行权限，其中u可替换为g代表当前用户组，a代表所有人。
+表示添加，-表示删除。x,r,w分别对应执行，读，写

#grep
这个命令非常强大，用到就写一点

```bash
grep -R 'string' dir/
```
在当前目录下所有文件里搜索string

```bash
grep [-acinv] [--color=auto] 'str-to-find' filename
-a:将二进制文件以文本文件的方式查找数据
-c:计算找到匹配字符串的次数
-i:忽略大小写
-n:顺便输出行号
-v:反向选择
```

#sort
排序

```bash
sort [-fbMnrtuk] [file or stdin]
-f:忽略大小写
-b:忽略最前面那部分空格
-M:以月份的名字来排序，如JAN这种
-n:文本转为数字的方式排序
-r:反向排序
-u:就是uniq，相同的数据中仅出现一行
-t:分隔符，配合-k使用
-k:分隔后以第几列排序
```
例子：

```bash
cat /etc/passwd | sort -t ':' -k 3 -n
```
以冒号分隔后第三列并以数字形式排序

#uniq
去重

```bash
uniq [-ic]
-i:忽略大小写
-c:进行计数
```

#wc
统计行或单词、字符数量

```bash
wc [-lwm]
-l:列出行数
-w:列出单词数
-m:列出字符数
```

#cut
类似split功能

```bash
echo $PATH | cut -d ':' -f 1,2
```
将PATH以冒号分割，输出第1个元素和第2个元素

```bash
export | cut -c 12-
```
-c处理排列整齐的输出，12-表示输出第12个字符以后的内容，12-20输出第12到20字符的内容

cut命令在处理多空格相连的数据时不好用

#scp
在两个host之间传输文件

```bash
scp source_file_in_local user@host:save_to_path
```

#less
查看文件的一种方式

```bash
less filename
-N:显示每行行号
-i:搜索忽略大小写
space:向下翻一页
b:向上翻一页
q:退出
```
很多vim的命令也可以用

#md5sum
查看文件的MD5值

```bash
md5sum filename
```

#man ascii

查看所有ascii码，方便查阅

#Ctrl+C
结束当前进程，不可恢复

#Ctrl+Z
暂停当前进程，可以恢复

#Ctrl+U
删除当前命令输入
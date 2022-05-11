# Linux实操篇

## Linux常用目录结构

### /bin 

 Binary的缩写，存放着最经常使用的命令

### /sbin    

s是Super User的意思，存放着系统管理员使用的系统管理程序

### /home

存放着普通用户的主目录

### /root

超级权限者（系统管理员）的用户主目录

### /etc

所有的系统管理所需的配置文件和子目录，例如安装了mysql，该目录就会有mysql.conf

### /usr

这是一个非常重要的目录，用户的很多应用程序和文件都放在这个目录下

### /media

linux系统会自动识别一些设备，例如u盘，光驱等等，当识别后，linux会把识别的设备挂载在这个目录下

### /mnt

系统提供该目录是为了让用户挂载临时的文件于该目录，我们可以将外部的存储挂载在/mnt上，然后进入该目录就可以查看里面的内容了

### /opt

这是给主机额外的安装软件所存放的目录（存放软件安装包）

### /usr/local

软件安装的目标目录（软件安装到该目录）

## Vi和Vim编辑器

### Vi和Vim的三种模式

![image-20220510211241014](E:\GitHub\JAVA-note\typora-user-images\image-20220510211241014.png)

### Vi和Vim主要的快捷键

![image-20220510230304869](E:\GitHub\JAVA-note\typora-user-images\image-20220510230304869.png)



## 开机、重启和用户登录注销

### 关机&重启命令

![image-20220510231601144](E:\GitHub\JAVA-note\typora-user-images\image-20220510231601144.png)

![image-20220510231631817](E:\GitHub\JAVA-note\typora-user-images\image-20220510231631817.png)

### 用户登录&注销

![image-20220510232645539](E:\GitHub\JAVA-note\typora-user-images\image-20220510232645539.png)

## 用户管理

### 添加用户

![image-20220511084132081](E:\GitHub\JAVA-note\typora-user-images\image-20220511084132081.png)

![image-20220511084150545](E:\GitHub\JAVA-note\typora-user-images\image-20220511084150545.png)

![image-20220511084208162](E:\GitHub\JAVA-note\typora-user-images\image-20220511084208162.png)

### 指定/修改密码

![image-20220511084356012](E:\GitHub\JAVA-note\typora-user-images\image-20220511084356012.png)

![image-20220511084400823](E:\GitHub\JAVA-note\typora-user-images\image-20220511084400823.png)

### 删除用户

![image-20220511084500609](E:\GitHub\JAVA-note\typora-user-images\image-20220511084500609.png)

### 查询用户信息指令

![image-20220511084629914](E:\GitHub\JAVA-note\typora-user-images\image-20220511084629914.png)

![image-20220511084646656](E:\GitHub\JAVA-note\typora-user-images\image-20220511084646656.png)

### 切换用户

![image-20220511084734801](E:\GitHub\JAVA-note\typora-user-images\image-20220511084734801.png)

![image-20220511084855016](E:\GitHub\JAVA-note\typora-user-images\image-20220511084855016.png)

### 查看登录用户

#### 基本语法 

#### whoami/who am i

### 用户组

#### 新增组 

groupadd 组名

#### 删除组

groupdel 组名

#### 案例

![image-20220511085505639](E:\GitHub\JAVA-note\typora-user-images\image-20220511085505639.png)

#### 修改用户的组

![image-20220511085608527](E:\GitHub\JAVA-note\typora-user-images\image-20220511085608527.png)

### 用户和组相关文件

#### /etc/passwd文件

![image-20220511085843455](E:\GitHub\JAVA-note\typora-user-images\image-20220511085843455.png)

#### /etc/shadow文件

![image-20220511085928881](E:\GitHub\JAVA-note\typora-user-images\image-20220511085928881.png)

#### /etc/group文件

![image-20220511090340684](E:\GitHub\JAVA-note\typora-user-images\image-20220511090340684.png)



## 实用指令

### 指定运行级别

![image-20220511115852605](E:\GitHub\JAVA-note\typora-user-images\image-20220511115852605.png)

![image-20220511115951883](E:\GitHub\JAVA-note\typora-user-images\image-20220511115951883.png)![image-20220511115955429](E:\GitHub\JAVA-note\typora-user-images\image-20220511115955429.png)

### 帮助指令

![image-20220511120100876](E:\GitHub\JAVA-note\typora-user-images\image-20220511120100876.png)

![image-20220511120103324](E:\GitHub\JAVA-note\typora-user-images\image-20220511120103324.png)

### ls指令

![image-20220511120135348](E:\GitHub\JAVA-note\typora-user-images\image-20220511120135348.png)

### cd指令

![image-20220511120213998](E:\GitHub\JAVA-note\typora-user-images\image-20220511120213998.png)

![image-20220511120230339](E:\GitHub\JAVA-note\typora-user-images\image-20220511120230339.png)

### mkdir指令

![image-20220511120308167](E:\GitHub\JAVA-note\typora-user-images\image-20220511120308167.png)

![image-20220511120330237](E:\GitHub\JAVA-note\typora-user-images\image-20220511120330237.png)

### rmdir指令删除空目录

![image-20220511120424630](E:\GitHub\JAVA-note\typora-user-images\image-20220511120424630.png)

### touch指令

![image-20220511120549170](E:\GitHub\JAVA-note\typora-user-images\image-20220511120549170.png)

![image-20220511120551544](E:\GitHub\JAVA-note\typora-user-images\image-20220511120551544.png)

### cp指令

![image-20220511120626799](E:\GitHub\JAVA-note\typora-user-images\image-20220511120626799.png)

![image-20220511120642378](E:\GitHub\JAVA-note\typora-user-images\image-20220511120642378.png)



![image-20220511120917603](E:\GitHub\JAVA-note\typora-user-images\image-20220511120917603.png)

### rm指令



![image-20220511121058740](E:\GitHub\JAVA-note\typora-user-images\image-20220511121058740.png)

![image-20220511121100993](E:\GitHub\JAVA-note\typora-user-images\image-20220511121100993.png)

![image-20220511121152256](E:\GitHub\JAVA-note\typora-user-images\image-20220511121152256.png)

### mv指令

![image-20220511121306068](E:\GitHub\JAVA-note\typora-user-images\image-20220511121306068.png)

复制到相同位置则是重命名，复制到其他位置，在最后的‘/’后也可以重命名

### cat指令

![image-20220511121414609](E:\GitHub\JAVA-note\typora-user-images\image-20220511121414609.png)

![image-20220511121416572](E:\GitHub\JAVA-note\typora-user-images\image-20220511121416572.png)

![image-20220511121430171](E:\GitHub\JAVA-note\typora-user-images\image-20220511121430171.png)

### more命令

![image-20220511121521269](E:\GitHub\JAVA-note\typora-user-images\image-20220511121521269.png)

### less指令

![image-20220511121612411](E:\GitHub\JAVA-note\typora-user-images\image-20220511121612411.png)

### echo指令

![image-20220511121654058](E:\GitHub\JAVA-note\typora-user-images\image-20220511121654058.png)

### head指令

![image-20220511121712959](E:\GitHub\JAVA-note\typora-user-images\image-20220511121712959.png)

### tail指令

![image-20220511121745102](E:\GitHub\JAVA-note\typora-user-images\image-20220511121745102.png)

### '>'指令和'>>'指令

![image-20220511121839406](E:\GitHub\JAVA-note\typora-user-images\image-20220511121839406.png)



### ln指令

![image-20220511200355042](E:\GitHub\JAVA-note\typora-user-images\image-20220511200355042.png)

### history指令

![image-20220511200452387](E:\GitHub\JAVA-note\image-20220511200452387.png)

## 时间和日期类

### 显示当前日期

![image-20220511200608500](E:\GitHub\JAVA-note\typora-user-images\image-20220511200608500.png)

### 设置当前日期

![image-20220511200717317](E:\GitHub\JAVA-note\typora-user-images\image-20220511200717317.png)

### cal指令

![image-20220511200749666](E:\GitHub\JAVA-note\typora-user-images\image-20220511200749666.png)

## 搜索查找类

### find指令

![image-20220511200919309](E:\GitHub\JAVA-note\typora-user-images\image-20220511200919309.png)

![image-20220511200938944](E:\GitHub\JAVA-note\typora-user-images\image-20220511200938944.png)

![image-20220511200955133](E:\GitHub\JAVA-note\typora-user-images\image-20220511200955133.png)

### locate指令

![image-20220511201054487](E:\GitHub\JAVA-note\typora-user-images\image-20220511201054487.png)

先执行updatedb再执行locate指令

### grep指令和管道符号|

![image-20220511201243435](E:\GitHub\JAVA-note\typora-user-images\image-20220511201243435.png)

![image-20220511201257443](E:\GitHub\JAVA-note\typora-user-images\image-20220511201257443.png)

## 压缩和解压类

### gzip/gunzip指令（压缩完原文件会消失/解压完压缩文件会消失）

![image-20220511201412415](E:\GitHub\JAVA-note\typora-user-images\image-20220511201412415.png)

### zip/unzip指令（压缩完原文件不会消失/解压完压缩文件不会消失）

![image-20220511201548334](E:\GitHub\JAVA-note\typora-user-images\image-20220511201548334.png)

![image-20220511201711342](E:\GitHub\JAVA-note\typora-user-images\image-20220511201711342.png)

### tar指令

![image-20220511201809770](E:\GitHub\JAVA-note\typora-user-images\image-20220511201809770.png)

![image-20220511201824613](E:\GitHub\JAVA-note\typora-user-images\image-20220511201824613.png)




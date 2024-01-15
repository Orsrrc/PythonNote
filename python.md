# 变量

在python中不需要对变量的类型进行定义

在使用时直接定义

变量指代内存中的内存空间

# 面向对象

关注谁能完成某一功能  函数 类 可能是由别的人制作



# 面向过程

怎么做？自己亲自做



# 类

一类的统称  抽象概念  特征一样

- 特征分类
  - 状态
    - 信息  能变
      - 成员变量
  - 行为
    - 能做什么
      - 成员方法  函数

统称为类的成员



## 定义（definenation）

大驼峰命名规则

```python
class Cat:
  pass
```

```python
class MyName:
  pass
```

复合词组  首字母大写

## 类成员——成员变量

```python
class Cat: #在python中创建对象时自动调用的方法叫魔术方法
 	def __init__(self): #公有属性
    self.type = '波斯猫'
    self.name = None #名字可变  
    def __str__(self): #打印时调用
      return "打印显示信息"
```

```py	
cat1 = Cat()#创建对象  调用构造函数
cat1.type#取值
cat1.name = '小黑' #赋值 调用
#创建对象私有属性  不在类定义中使用
cat1.cloth = '衣服' #创建对象时定义
```

与C++不同 C中要求构造函数与类名相同 且仅有一个构造函数

ptyhon中可以看成有多个内置的构造函数 名字固定 在触发函数的调用条件的时候自动调用  如___init__\_在创建对象时调用

\_\_str\_\_在打印对象地址的时候自动调用

## 类成员——成员方法

方法 即写在类中的函数

```python
class Cat:
  def eat(self): #猫的方法
    print("猫吃鱼")
  def climb(self):
    print("猫会爬树"）
  def sleep(self, 形参1, 形参n, time)
    print("猫会睡觉，睡了%d秒"%time)
cat1 = Cat()
cat1.climb()#调用方法
```





# 对象

具体解决事物的概念  

格式；

​		变量 = 类名()

创建对象不限制数量

***对象与类的关系类似个性与共性的关系***

```python
cat1 = Cat()
cat2 = Cat()
cat3 = Cat()
```

对象与变量都指代一块内存区域 对象名 和变量名都是内存区域的起始地址







# 成员方法与成员变量

1. 在成员方法中调用成员变量

   ```python
   class cat:
     def __init__(self):
       self.type = "波斯猫"
       self.name = None
       
     def introduce(self):
       print("我是一只%s, 我的名字是%s" (self.type, self.name))
       #成员方法中调用成员函数需要使用self对象
   		#类中的self均指向调用者对象
   ```

   

2. 在成员方法中调用独有属性

   ```python
   class cat:
     def __init__(self):
       self.type = "波斯猫"
       self.name = None
       
     def introduce(self):
       print("我的颜色是%s" (self.color))
   
   cat1 = cat()
   cat1.color = "red"
   cat1.introduce()
   
   #但若有别的对象调用color属性  由于这是cat1的独有属性  则会报错
   
   cat2.introduce() #error
   ```

   

3. 成员方法调用成员方法

   ```python
   class cat:
     def catch(self):
       #1.追逐
       self.run()
       #2.抓住
       self.grasp()
       #3.咬
       self.bite()
       
   
     def run(self):
       print("追逐")
     def grasp(self):
       print("抓住")
     def bite(self):
       print("咬")
       
   cat1.catch()
   ```

   self仅出现在成员方法中，指代执行该方法的对象

   

# "手机"案例

```python
#案例
#手机电量默认为100
#打游戏每次消耗电量10
#听歌每次消耗电量5
#打电话每次消耗电量4
#接电话每次消耗电量3
#充电可以为手机补充电量

import time

class Phone:

    def __init__(self):
        self.ElectricCharge = 100


    def Menu(self):
        print("*" * 10)
        print("1.玩游戏")
        print("2.听歌")
        print("3.打电话")
        print("4.接电话")
        print("5.充电")
        print("6.关机")
        print("*" * 10)

    def Selection(self):
        x = int(input())
        if x == 1:
            self.PlayGame()
        elif x == 2:
            self.LinstenMusic()
        elif x == 3:
            self.Call()
        elif x == 4:
            self.Pick()
        elif x == 5:
            self.BatteryCharge()
        elif x == 6:
            self.ShutDown()
        else:
            print("error!")

    def PlayGame(self):
        self.ElectricCharge -= 10
        print("玩游戏，手机电量%d" %self.ElectricCharge)

    def LinstenMusic(self):
        self.ElectricCharge -= 5
        print("听音乐，手机电量%d" %self.ElectricCharge)

    def Call(self):
        self.ElectricCharge -= 4
        print("打电话，手机电量%d" %self.ElectricCharge)

    def Pick(self):
        self.ElectricCharge -= 3
        print("接电话，手机电量%d" %self.ElectricCharge)

    def RunOut(self):
        if self.ElectricCharge == 0:
            print("电量耗尽，手机关机")
            return 1

    def BatteryCharge (self):
        print("充电中，当前电量%d" %self.ElectricCharge)
        while self.ElectricCharge != 100:
            self.ElectricCharge += 10
            time.sleep(10)

    def Open(self):
        self.flag = True
        while self.flag:
            if self.RunOut():
                break
            self.Menu()
            self.Selection()

    def ShutDown(self):
        print("确认关机吗？")
        if int(input()) == 1:
            self.flag = False
            print("关机~")

iphone = Phone()
iphone.Open()
```

pass是个关键字 在还未具体实现函数时使用





# 面向对象 

**三大特征  继承  封装 多态**

## 封装

不同访问权限的数据

不加关键字时 默认为public

```python
class Card:
  def __init__(self):
    self.card_id = None
    self.__pwd = None
    #__  两个下划线为私有   非成员函数不能访问
 	 
  def GetPassword(self):
    return self.__pwd
  
  def SetPassword(self, pwd):#需要形参的时候 self也必须存在
    self.__pwd = pwd
 
#此时不能直接访问pwd
c = Card()
c.__pwd = "123" #error
c.GetPassword(self)
c.SetPassword(c.GetPassword(self))

```

*** 封装对受访问保护的成员进行功能开放的控制达到用户数据不被非法访问的目的***

***用户在使用时不用在意被封装好的类的具体操作 只需要提供对应接口所需的变量即可***



在_\_init__()方法中添加多个参数  初始化时将数据给如即可

```python
class Cat:
  def __init__(self, type, name):
    self.__type = type
    self.__name = name

cat1 = Cat("波斯猫", "小黑")
```



## 继承

class 类名(父类名)

子类中无_\_init_\_(self)方法时 创建子类对象时默认调用父类中的_\_init__()方法

*** 多态是在继承的基础上实现的***

子类继承父类的方法后  可以在子类中重新对父类的方法进行重写  

编译器根据函数参数的不同等等特征  对函数进行调用



### 鸭子类型

```python
class Teacher:
  def teach(self):
    print("传授知识")
class Man(Teacher):
  def teach(self):
    print("传授python知识")
class Woman(Teacher):
  	def teach(self):
      print("传授JAVA知识")
class Father:
  	def teach(self):
      print("传授生活知识")

def Demo(self, teacher):
  teacher.teach()
  
Man = Man()
Demo(Man)# 编译通过

Father = Father()
Demo(Father) #编译通过


```

Python中未对函数传入参数的类型进行定义  只需求一个对象  这个对象可以是常用类型的变量 也可是一个自定义类型的变量
**只需要满足传入的对象能够完成函数方法中的指令即可 即只需要满足函数的使用即可  这里对Father类 不继承与Teacher 但满足调用关系  称该对象具备**鸭子类型**
**弱类型语言  都具有这种类型**

鸭子类型是一种特殊的多态  多态要求在类型上绝对匹配  而鸭子只要求在函数调用中满足对应的关系即可



# "反恐精英"案例



```python
#1.定义person 类 ，描述公共属性 life = 100 name 创建对象时给定
#2.定义主函数描述枪战过程  创建对象
#3.定义开枪方法，分成两个方法 也可以在父类中定义 方法中要传入被射击的对象

class Person:
    def __init__(self,Name):
        self.Name = Name
        self.__life = 100

    def GetLife(self):
        return self.__life

    def SetLife(self, life):
        self.__life = life

    def damage(self, source, target, DamageValue):
        pass

class Red(Person):

    __DamageValue = 40

    def GetDamageValue(self):
        return self.__DamageValue

    def damage(self,target, DamageValue):
        if self.GetLife() == 0:
            print("目标已死亡")
            return 0
        print("%s向%s开枪,造成了%d点伤害"%(self.Name, target, DamageValue))
        life = self.GetLife() - DamageValue
        if life <= 0:
            life = 0
        self.SetLife(life)
        print("%s的当前血量为%d" %(target, self.GetLife()))

class Blue(Person):
    __DamageValue = 30
    def GetDamageValue(self):
        return self.__DamageValue

    def damage(self, target, DamageValue):
        if self.GetLife() == 0:
            print("目标已死亡")
            return 0
        print("%s向%s开枪,造成了%d点伤害" % (self.Name, target, DamageValue))
        life = self.GetLife() - DamageValue
        if life <= 0:
            life = 0
        self.SetLife(life)
        print("%s的当前血量为%d" % (target, self.GetLife()))

def main():
    red1 = Red("小红")
    blue2 = Blue("小蓝")
    #print("%d" %(red1.GetLife()))
    red1.damage(blue2.Name,red1.GetDamageValue())

main()
#python中main函数并不是主动调用的
```





# 飞机大战 案例 

- 组成分析
  - 窗体
  - 背景
  - 玩家飞机
  - 敌人飞机
  - 子弹
  - ……
- 动作分析
  - 背景移动
  - 玩家跟随鼠标移动
  - 敌人飞机向下移动
  - 子弹向上移动
  - 敌机死亡后爆炸
  - ……
- 业务分析（制作阶段）
  - 游戏如何结束
  - 敌人飞机飞行速度
  - 子弹飞行速度





# 学员管理系统

#### 1.需求分析

界面：

- 增、删、改、查
- 显示所有学员信息
- 退出系统

步骤：

- 显示功能界面
- 用户输入功能序号
- 根据用户输入的功能序号，执行不同的功能（函数）
  - 输入判断
  - 定义函数
  - 调用函数



# 网络编程 (传输层)

协议 TCP  、 UDP

## 端口

N多个网络程序 根据端口号来分辨分发给哪一个网络进程



在一个局域网内

```python
PC1 往PC2发送 IP数据包
包内内容
destination ip address:PC2
destination port: 5678
source ip address:PC
source port: 8888
content : "你好"

交换机根据 目的ip 往目的主机内发包  目的主机在拆包后根据端口号将该数据报分发给网络进程
目标网络进程可以根据源IP与源端口号向发送方的网络进程发包
```

### 端口分类

- 知名端口
  - 规定好的端口 0~1023
    - 如21 FTP 的数据传输端口
    - 80端口的HTTP
- 动态端口 1024~65535
  - 进程死亡后  所占用的端口号也被释放

## SOCKET (插口)

套接字  进程间通信的一种方式

### 用法

导入socket模块

Import socket

创建客户端socket 对象

socket.socket(AddressFamily, Type)

- 参数说明
  - AddressFamily 表示IP地址类型， 分为IPV4和IPV6
    - Socket.AF_INET 代表IPV4
    - Socket.SOCK_STREAM 代表TCP
    - socket.SOCK_DGRAM 代表UDP
  - Type表示传输协议类型

​		





## UDP

```python
import socket
#创建一个UDP套接字
def main():
  udp_socket = socket.socket(socket.AF_INET, sokcet.SOCK_DGRAM)

#使用套接字收发数据
	udp_socket.sendto(需要byte类型#内容, #目的IP 端口 （元组）)
  udp_socket.sendto(b"hahaha", ("192.168.0.1", "8888"))
	
#关闭套接字
udp_socket.close()
  
if __name == "__main__":
  main()
```

**Teminal 运行.py**

**运行.py**

**python     .py**

**dhclient 重新分配ip** 



### 交互模式

python

Exit()

ipython 可以自动补全



type() 查看类型

type(b "100") return byte



```python
import socket
def main():
  udp_socket = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
```





# TCP

TCP网络应用程序开发分为:

- TCP客户端程序开发
  - 为客户端提供数据服务
- TCP服务端程序开发



## TCP客户端程序开发流程

创建客户端套接字对象socket() 并指定协议

建立连接 三次握手

发送数据  send 数据类型  二进制(byte)类型

接受数据

关闭套接字



## TCP服务端开发流程

准备套接字

绑定进程端口号

设置监听

接受建立连接

receive

send

关闭套接字



## 方法说明

- connect((host, port)  #元组) 表示和服务端套接字建立连接，host是服务器ip地址， port是应用程序的端口号
- Send(data) 表示发送数据 data类型为二进制数据  需要用encode方法将其转换
- Recv(buffersize) 接受数据. buffersize缓冲区大小  一般为1MB 



## 代码

```python
```



# vim

命令模式下 

V + < 整体缩进一个tab

V + > 整体空格一个tab

编辑模式下  ctrl + n 补全



# 爬虫

## 概念

模拟浏览器，发送请求，获取响应

网络爬虫 模拟客户端 发送网络请求 接受请求响应

爬虫只能获取客户端所展示出来的数据



## 作用

- 数据采集 录入数据库  机器学习等等
- 数据分析 挖掘



## 分类

- 被爬取网站的数量不同
  - 通用爬虫
  - 聚焦爬虫
- 是否爬取到目标信息
  - 功能性爬虫
    - 投票 点赞 
  - 数据增量爬虫
    - 招聘信息
- url地址和对应的页面内容是否改变
  - url变 内容也随之变化的数据增量爬虫
  - url地址不变， 内容都变化

## 流程

url_list -> 发送请求，获取响应->解析响应->保存数据

- 获取一个url
- 向url发送请求，并获取响应(需要http协议)
- 如果从响应中提取url 则继续发送请求获取响应
- 如果从响应中提取数据，则将数据进行保存



## http与https

http 80

https 443

http + ssl = https

安全套接字 ssl

## 请求头和响应头

方法 /路径/ 协议版本

请求头

- Content-Type 内容类型
- Host (主机和端口号)  域名
- Connection (链接类型)
  - Keep-live 持续连接  否则 每发送一次数据包 就建立和断开一次tcp链接 效率低
- Upgrade-Insecure-Requests (升级为HTTPS请求)
  - 用http链接时  若该网站支持https 则浏览器自动重定向为https请求
- **User-Agent** (用户代理)
  - 发送请求的机器的information
    - Webkit 内核 浏览器引擎
    - 用information 伪装成一个正常的用户

渲染 ：模版 从数据库中传入参数到模版中 然后返回一个完整的文件

- **Referer** (页面跳转处)
  - 从哪一个页面发起的请求 检查请求是否合法
  - 防盗链(图片/视频)
- **Cookie** (Cookie)
  - 保持回话  保持权限 状态保持
  - 具有时效性 判断是否为某一用户
- Authorization(用于表示HTTP协议中需要认证资源的认证信息，如前边web课程中用于jwt认证)
  - 有账户 密码

响应头

- Set-Cookie （对方服务器设置cookie到用户浏览器的缓存）





### 3. 常见的响应状态码

- 200：成功
- 302：跳转，新的url在响应的Location头中给出
- 303：浏览器对于POST的响应进行重定向至新的url
- 307：浏览器对于GET的响应重定向至新的url
- 403：资源不可用；服务器理解客户的请求，但拒绝处理它（没有权限）
- 404：找不到该页面
- 500：服务器内部错误
- 503：服务器由于维护或者负载过重未能应答，在响应中可能可能会携带Retry-After响应头；有可能是因为爬虫频繁访问url，使服务器忽视爬虫的请求，最终返回503响应状态码

在爬虫中，可能该站点的开发人员或者运维人员为了阻止数据被爬虫轻易获取，可能在状态码上做手脚，也就是说返回的状态码并不一定就是真实情况，比如:服务器已经识别出你是爬虫，但是为了让你疏忽大意，所以照样返回状态码200，但是响应体重并没有数据。

**所有的状态码都不可信，一切以是否从抓包得到的响应中获取到数据为准**



















# GIL全局解释器锁

```python
#单线程死循环  占满CPU
while True:
  pass
```




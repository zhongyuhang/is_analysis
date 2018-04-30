# 实验4:图书管理系统顺序图绘制

|    学号   |       班级       |      姓名     |
|:-------:|:------------- | ----------:|
|   201510414227  |     软工2班     |   钟宇航   |

### 1.个人图书馆超级管理员部分
#### 1.1PlantUML源码如下：
````
@startuml
box "__超级管理员__用例"
hide footbox

actor __超级管理员__ as superManager
actor __管理员__ as manager
participant __读者__ as info

activate superManager
superManager -> manager : 输入管理员账号
activate manager
manager -> info :管理读者账号
deactivate manager

activate info

info --> superManager :反馈信息给管理员及超级管理员
end box
@enduml
````

#### 1.2顺序图如下：
![](./fhr1.png '描述')

### 2.普通管理员部分
#### 2.1PlantUML源码如下：
````
@startuml
hide footbox
autonumber
actor __管理员__ as manager
actor __读者__ as reader
participant __读者信息__ as readerInfo

activate manager
manager -> reader : 输入读者账号
activate reader
reader -> readerInfo :私人信息
reader -> readerInfo :修改个人信息
readerInfo --> manager :确认修改信息
deactivate reader

activate readerInfo

readerInfo --> manager :存储信息

manager -> readerInfo:获取借阅情况
manager <- readerInfo:借书、还书信息

@enduml
````

#### 2.2顺序图如下：
![](./fhr2.png '描述')

### 3.预定图书部分
#### 3.1PlantUML源码如下：
````
@startuml

hide footbox
title __预定图书__ 用例
actor 读者 
boundary 权限判断
control 业务控制
database 数据库
autonumber
activate 权限判断
	读者 -> 权限判断 :  输入账号信息
	activate 业务控制
		权限判断 -> 业务控制 : 获取账号信息
deactivate 权限判断
		activate 数据库
			业务控制 -> 数据库 : 比对账号密码合法性
			数据库 --> 业务控制 : 账号合法

			读者 -> 业务控制 : 输入预定图书信息
			业务控制 -> 数据库 : 增加预定信息
			数据库 -> 业务控制 : 返回操作结果
		deactivate 数据库
	业务控制 -> 读者 : 返回预定图书结果
	deactivate 业务控制

@enduml
````

#### 3.2顺序图如下：
![](./fhr3.png '描述')

### 4.详细图书查询部分
#### 4.1PlantUML源码如下：
````
@startuml
hide footbox
title __详细图书查询__用例
autonumber
actor 读者 as reader
control 查询 as search
entity 查询方式 as searchway
control 书名查询 as bookname
control ISBN查询 as isbn
database 数据库 as db
participant 查询结果 as results
activate reader
reader -> search:查询图书信息
activate search
search -> searchway:输入查询方式
activate db
activate searchway
activate isbn
searchway-> isbn:根据ISBN进行查询
activate bookname

searchway-> bookname:根据书名进行查询
isbn -> db:查询
deactivate isbn

bookname -> db:查询
deactivate bookname

db->results:得到结果
activate results
deactivate db
deactivate search
results -> reader:返回结果
deactivate results
@enduml
````

#### 4.2顺序图如下：
![](./fhr4.png '描述')

### 5.借阅图书部分
#### 5.1PlantUML源码如下：
````
@startuml
hide footbox
title __借阅图书__
autonumber
actor __读者__ as reader
participant 借书登记 as chioce
participant 系统判断 as inter
participant 借书记录 as bookrecord
activate reader
reader ->chioce :选择登记

activate chioce
chioce -> inter:借阅内容
activate inter
inter -> bookrecord :添加借阅记录
deactivate inter
activate bookrecord

bookrecord -> reader :确认借书登记

@enduml
````

#### 5.2顺序图如下：
![](./fhr5.png '描述')

### 6.归还图书部分
#### 6.1PlantUML源码如下：
````
@startuml

hide footbox
autonumber
title __归还图书__ 用例
actor 管理员 as manager
boundary 账号判断 as account
control 业务判断  as business
database 数据库 as db

activate account
	manager -> account :  输入读者账号信息
	activate business
		account -> business : 获取账号信息
deactivate account
		activate db
			business -> db : 比对账号密码合法性
			db --> business : 账号合法


			manager -> business : 输入归还图书信息
			business -> db : 删除借阅信息
			business -> db : 修改图书库存
			db -> business : 返回操作结果
		deactivate db
	business -> manager : 返回归还结果
	deactivate db
	
@enduml
````

#### 6.2顺序图如下：
![](./fhr6.png '描述')


# ʵ��3��ͼ�����ϵͳ�������ģ
|ѧ��|�༶|����|
|:-------:|:-------------: | :----------:|
|201510414227|���(��)15-2|���|
## 1. ͼ�����ϵͳ����ͼ
### 1.1 ��ͼPlantUMLԴ�����£�

``` class
@startuml
package "Books Managerment System" {
class ԤԼ�鼮 {
  BookNo
  StudentNo
  BookingTime
}
class ����鼮 {
  BookNo
  StudentNo
  LendTime
  LeastTime
}
class �黹�鼮 {
  BookNo
  StudentNo
  ReturnTime
  Fine

}
class �鼮 {
   BookNo
   BookName
   Arthur
   ISBN
   Publish
   price
   BookState
   BookClass
}


class ������ {
   PersonNo
   Password
   PersonInfo
}
class ��ͨ����Ա{
    AdminID
    Password
 }
class ϵͳ����Ա {
   RootId
   Password

}

������"1" -- "0..*"�鼮:��ѯ�鼮
������"1" -- "0,1..2"ԤԼ�鼮:ԤԼ����
������"1" -- "0,1..2"����鼮:����
������"1" -- "0..*"�黹�鼮:�黹�鼮�����ɷ���

�鼮    "*"--"1" ��ͨ����Ա:��ɾ�Ĳ�
����鼮"*"--"1" ��ͨ����Ա:����鼮�������鼮
�黹�鼮"*"--"1" ��ͨ����Ա:�黹�鼮�������鼮�����ڷ���
ԤԼ�鼮"*"--"1" ��ͨ����Ա:��ѯԤԼ��ȡ��ԤԼ
������  "*"-"1"  ϵͳ����Ա:��ɾ�Ĳ�
��ͨ����Ա -- ϵͳ����Ա:��ɾ�Ĳ�

}
@enduml
```

### 1.2. ��ͼ���£�


![class](class.png)
24


## 2. ͼ�����ϵͳ�Ķ���ͼ

### 2.1 �����鼮�Ķ���ͼ

#### Դ�����£�

```class 

@startuml

object ����鼮{
    BookNo=123456
    PersonNo=201510414227
    LendTime=2018-05-17
    LeastTime=2018-6-16
}
@enduml


``` 

#### ����ͼ���£�

![class](borrow.png)



### 2.2 ��ԤԼ�鼮�Ķ���ͼ

#### Դ�����£�

``` class

@startuml

object ԤԼ�鼮{
   BookNo = 123456
   PersonNo = 201510414227
   BookingTime = 2018-4-20
}
@enduml


``` 

#### ����ͼ���£�

![class](lend.png)
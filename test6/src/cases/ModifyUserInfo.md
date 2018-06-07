<!-- markdownlint-disable MD033-->
<!-- 禁止MD033类型的警告 https://www.npmjs.com/package/markdownlint -->

# “修改用户信息”用例 [返回](../../README.md)
## 1. 用例规约

|用例名称|修改用户信息|
|-------|:-------------|
|功能|修改用户的GitHub用户名称|
|参与者|已登录用户|
|前置条件|必须先登录，并且查看用户现有的GitHub用户名|
|后置条件| |
|主事件流| 1.用户填写GitHub用户名称 <br/> 2.用户提交修改信息 <br/>3.系统存储修改后的GitHub用户名称|
|备选事件流|1a.如果用户输入的GitHub用户名称为空 <br/>1.系统清空用户的GitHub用户名称|

## 2. 业务流程
无

## 3. 界面设计
- 界面参照:https://github.com/zhongyuhang/is_analysis/blob/master/test6/src/ui/updateInfo.png
- API接口调用
    - 接口1：[getUserInfo](../mapper/getUserInfo.md)
    - 接口2：[setUserInfo](../mapper/setUserInfo.md)
    
## 4. 算法描述
无
    
## 5. 参照表
- [USERS](../../DataDesign.md/#USERS)
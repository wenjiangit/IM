### Class变更须知：

本次变更分为服务器和手机端项目都有变更

PS: 手机端数据库查看工具：http://sqlitebrowser.org/



**服务器端项目**

都是bean包下文件变更，同时也都是新增；无修改。

net.qiujuer.web.italker.push.bean.api.base:

* PushModel.class

net.qiujuer.italker.factory.model.card:

* ApplyCard.class
* GroupCard.class
* GroupMemberCard.class
* MessageCard.class



**手机端项目**

都是model目录下文件变更，直接copy对应文件夹覆盖即可。

net.qiujuer.italker.factory.model.api:

* PushModel.java

net.qiujuer.italker.factory.model.card:

* ApplyCard.java
* GroupCard.java
* GroupMemberCard.java
* MessageCard.java
* UserCard.java 添加了注释

net.qiujuer.italker.factory.model.db:

* AppDatabase.java 修改了数据文件版本
* Group.java
* GroupMember.java
* Message.java
* Session.java
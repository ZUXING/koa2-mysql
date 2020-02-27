#NodeMySQLBackstage
暂且把这个个人项目叫**NodeMySQLBackstage**吧，我还没想到更好的名字。
这是一个基于koa2、mysql的后台框架，它允许用户直接在浏览器的URL输入栏来操作MySQL数据库，并且将返回的JSON数组显示在浏览器上。同样，因为所有的MySQL指令都在URL上，我们还可以通过Axios异步请求数据库的内容。

###安装
直接复制下来，从命令行输入npm install就可以。如果复制后还有node_module文件夹，请删除。一定不要改动项目结构，但是部分文件需要你修改，便于连接你的数据库。
./app.js ->此项目的端口号，切记不能和数据库的端口号一样，默认是3000。
./js/db_connect.js ->这里面需要你填写连接数据库的用户名、密码、地址、端口号等
安装完成以后，输入node app.js即可启动。

###使用
假设你的MySQL服务器地址是http://127.0.0.1:3306，刚刚部署的项目地址是http://127.0.0.1:3000。
直接执行SQL语句：http://127.0.0.1:3000/runsql/你的SQL语句
查询数据库：http://127.0.0.1:3000/SHOW%20DATABASES
>**为什么是SHOW%20而不是SHOW空格**
>当你在地址栏输入中文，或者一些符号的时候，它们会被浏览器自动转义为URL形式。所以你不用担心%20这样的东西混入进去。
>你直接输入SHOW DATABASES，它会自动转义的。

新建数据库：http://127.0.0.1:3000/CREATE%20DATABASE%20数据库名
查询某个数据库的表：http://127.0.0.1:3000/数据库名
添加新的表：http://127.0.0.1:3000/数据库名/CREATE%20TABLE%20\`表名\`(列名、参数等)
执行Select语句：http://127.0.0.1:3000/数据库名/SELECT语句...
>**注意**
>执行上面的Select语句时，一定要有WHERE子句，哪怕没有什么WHERE条件也要WHERE 1。

目前只做了这么多，也没有足够的测试，对于用户的错误输入有duang掉的可能。欢迎大家多多提意见和建议。这个项目有空就一直更新，没空的话也不要催，我还没找到工作，有济南的好的前端工作私聊一下我，谢谢。由于我刚刚接触Node.JS，这个项目也有很多不完善的地方。欢迎大家加好友（QQ：1992599855，邮箱：[zuxingv@foxmail.com](mailto:zuxingv@foxmail.com)），自己复制一份拿去改着玩也行。
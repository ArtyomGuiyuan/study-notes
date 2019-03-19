# html表单补充

## html表单标签
> 关于表单标签的补充内容

* action 提交的地址 后端程序员给的
  目前只要有表单 就必须有form<br>
  get方式提交,参数在地址栏显示,不安全<br>
  post方式提交,参数在请求体保存,相对安全
  

  

* 单行文本输入<br> 
  例如用户名和密码

	`
	用户名: <input type="text" name="username" value="李四"  readonly> 
	`
	`
	密码: <input type="password" name="password">
	`
	
	readonly 只读 / disabled 无法选定 (较少使用)
* 单选 <br>
  例如性别

	`
	性别:男:<input  type="radio" name="sex" value="0">
	`
	`
	女:<input checked type="radio" name="sex" value="1">
	`
	
	checked 默认选中
* 多选<br>
  例如爱好
	
	`
	篮球 <input checked type="checkbox" name="like" value="001">
	`
	`
	足球 <input type="checkbox" name="like" value="002">
	`
	`
	乒乓球 <input checked type="checkbox" name="like" value="003">
	`

	label可以把内容和标签包括起来
* 下拉框<br>
  例如工作年龄
	```
    <select name="exp">
	<option value="100">无</option>
	<option value="101" selected>1~3</option>
	<option value="102">3~5</option>
	</select>
	```

* 上传图片<br>
  例如头像

    `
	input type="file" name="avatar">
	`
* 文本框<br>
  例如
	`
	<textarea name="bak" cols="30" rows="5"></textarea>
	`

* 提交按钮
	`
	<input type="submit" value="提交">
	`
## iframe 画中画
>用实现在当前页面包含其他页面



## a标签跳转

* target = "_self" 当前页面跳转
* target = "_black" 新窗口跳转
* target = "_parent" 父类窗口刷新
* target = "_top" 顶级父类窗口刷新

# git
>版本控制器
## 基本命令
* 在文件夹内输入 git init 初始化仓库
* git status 查看文件是否被暂存或者存储
* git add . 把文件存入暂存区
* git commit-m'xxxx'把文件存入存储区
* 添加远程源将本地仓库和远程仓库建立连接
  git remote add origin https://github.com/nevermo2013/noteH5.git
* git push -u origin master
  把本地文件提到远程github
* 第二次暂存提交后 不需要再配置源信息 提交只需要git    push即可
# github
>前端最重要的网站.

* 网址 https://github.com/
* 点击右上角 +  new  repository
* 重要: Repository name不能写中文
* 不要勾选 "Initialize this repository with a README" 


## 遇到的问题

+ 
	git remote add origin**************

    fatal: remote origin already exists.

    （报错远程起源已经存在。）

   解决方法: 

1、先输入 git remote rm origin

2、再输入 git remote add origin**************

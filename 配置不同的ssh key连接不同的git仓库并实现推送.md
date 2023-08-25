1.清除已有的global全局设置（针对曾经设置过的用户，如果没有设置过则不用清除）
使用过下面的指令清除设置过的全局的user.name 和 user.email

设置：

```bash
$ git config --global user.name   "你的名字"
$ git config --global user.email  "你的邮箱"
```

清除：

```bash
$ git config --global --unset user.name "你的名字"
$ git config --global --unset user.email "你的邮箱"
```

**2.生成指定名字的SSH公钥** ——> 这也是关键

```bash
$ssh-keygen -t rsa -C ‘123456@qq.com’ -f ~/.ssh/gitee_id_rsa
```

```bash
$ssh-keygen -t rsa -C ‘123456@qq.com’ -f ~/.ssh/gitee_id_rsa
```

生成不同的ssh，配置给不同的平台，如gitee，gitlab，github等

**3.创建config文件** ——> **主要就是这里**

在 ~/.ssh 目录【C:\Users\用户名.ssh】下新建一个config文件，添加如下内容（其中Host和HostName填写git服务器的域名，IdentityFile指定私钥的路径）

```bash
# gitee
Host gitee.com
HostName gitee.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/gitee_id_rsa
# github
Host github.com #域名
HostName github.com  #域名
PreferredAuthentications publickey
IdentityFile ~/.ssh/github_id_rsa
```

> 注意：就算gitee_id_rsa、github_id_rsa这些文件的内容一样也没关系，只要保证本地的key和官网的内容一样即可！

4.给特定的仓库单独配置用户名和邮箱

（否则推送会报错：Author identity unknown Please tell me who you are.，但是克隆不会报错）

在仓库进行git init之后进行配置即可：

```js
git config user.email "your-email@example.com"
git config user.name "Your Name"
```

5.使用idea或者vscode或者命令行的方式进行仓库的推送提交等操作！

```bash
git config user.email "郝文海"
git config user.name "1558637209@qq.com"
```

```bash
git config user.email "haowenhai"
git config user.name "haowenhai@songshuai.com"
```


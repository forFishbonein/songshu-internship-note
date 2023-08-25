报错：

![image-20230530232043798](https://aronimage.oss-cn-hangzhou.aliyuncs.com/img/image-20230530232043798.png)

1.原因：因为仓库的开发者是没有master权限的，需要新建分支然后再上传代码

2.解决方案：

```bash
#查看当前所处分支
git branch
#新建git分支名为dev，并切换到新建分支dev上
git checkout -b dev
#查看是否切换到新建分支dev
git branch
#添加
git add .
#提交
git commit -m '提交文件时的说明'
#将文件推送到dev分支
git push origin dev
```


## 给傻子的git教程

### 把文件上传到github上。
1. 首先在github上创建一个git仓库，注意：初始化的时候，不要创建readme文件。

2. 在本地初始化一个仓库，点击右上角的三个点More actions,选择Remote，点击Add remote，在输入框里输入仓库的url，也可以点击Add remote from Github.选择一个仓库，这个仓库就是你要存储删除上传的文件的位置。

3. 点击commit按钮，然后点击publish branch，这样文件就被上传到指定的仓库里去了。

4. 如果在上传到github上的时候报错，说连接不上服务器，可以配置一下代理地址。

```bash
git config --global http.proxy http://127.0.0.1:1080
git config --global https.proxy http://127.0.0.1:1080

```

然后取消代理
```bash
git config --global --unset http.proxy
git config --global --unset https.proxy
```
再次点击publish  branch,文件即可上传到github上
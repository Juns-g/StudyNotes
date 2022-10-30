## 搭建hexo博客

首先，注册一个Github或者Gitee账号。

```powershell
npm install -g hexo-cli   #安装hexo
hexo -v   #查看hexo版本

# 现在创建一个文件夹，比如blog，然后在命令行进入这个文件夹
hexo init myblog  # 这里的myblog是将要生成的文件夹名字，可以换成其他的  ！！！暂时先用下面的命令！！！
# ！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！
cd myblog
hexo generate  # 生成各种web资源
hexo server   # 启动本地服务
# 现在浏览器访问http://localhost:4000即可

hexo new "文章名"  # 新建文章
# 用编辑器编辑内容
hexo clean
hexo generate
hexo server

npm install --save hexo-deployer-git  # 安装hexo的git插件
# 设置_config.yml
	deploy:
  		type: git
  		repository: #替换成项目地址#
hexo deploy  # 部署
# 要是同步到Gitee仓库，需要更新；GitHub会自动更新
```

原理：利用Node.js在本地渲染以后，生成静态资源，上传至GitHub或者码云

另外，也可以换主题，一般都在GitHub上开源

```powershell
git clone https://github.com/litten/hexo-theme-yilia.git themes/yilia
# 修改一下_config.yml的theme
# 然后还是那几个命令
hexo clean
hexo generate
hexo server
```

---

！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！！

> hexo init xxxx实际上是如下命令的集成：

```powershell
git clone https://github.com/hexojs/hexo-starter.git myblog
cd myblog
git submodule init
git submodule update
npm i
```

> 在我写这个文档的时候（2020.12.11）发现21小时前的一个更新hexo-starter的作者把themes下的文件清空了，导致了后面更换主题后执行任何hexo操作都会出现如下错误：
>
> ERROR {
> err: [Error: EISDIR: illegal operation on a directory, read] {
>  errno: -4068,
>  code: 'EISDIR',
>  syscall: 'read'
> }
> } Plugin load failed: %s hexo-theme-landscape
>
> **因此此处暂时先将hexo init xxxx替换成如下命令**（将原仓库替换成一个镜像仓库）：

```powershell
git clone https://gitee.com/weilining/hexo-starter.git myblog
cd myblog
git submodule init
git submodule update
npm i
```

---

---


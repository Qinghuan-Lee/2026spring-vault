# 学习网站
> https://learngitbranching.js.org/?locale=zh_CN

# commit 提交
>git commit 
>commit 把 ...托付给....
  
# branch 分支
> git branch
> branch 分支


> `*` 表示当前所在的分支

# checkout 登出
> checkout 
> 结账  签出


# 上传github


>  暂存  git add
>  提交  git commit
>  推送  git push


把本地文件上传到 GitHub 指定仓库，主要分两种情况：

---

**情况一：仓库已存在于 GitHub，本地还没有**

1. 先克隆远程仓库到本地：`git clone https://github.com/用户名/仓库名.git`
2. 进入仓库目录：`cd 仓库名`
3. 把你要上传的文件复制到这个目录下
4. 暂存文件：`git add .`（全部）或 `git add 文件名`（指定文件）
5. 提交：`git commit -m "提交说明"`
6. 推送：`git push origin main`（分支名视情况改为 `master` 或其他）

---

**情况二：本地已有项目，想推送到 GitHub 新建/已有的空仓库**

1. 进入本地项目目录：`cd 你的项目路径`
2. 初始化 Git：`git init`

```
PS D:\go-chat> git init
Initialized empty Git repository in D:/go-chat/.git/

```



3. 关联远程仓库：`git remote add origin https://github.com/用户名/仓库名.git`
无事发生

4. 暂存文件：`git add .`
5. 提交：`git commit -m "首次提交"`
6. 推送：`git push -u origin main`

如果远程仓库非空（比如建仓库时勾了 README），先拉取再推送：`git pull origin main --rebase`，然后再 `git push`。

---

**补充几个常用点：**

- 首次使用需要配置身份：`git config --global user.name "你的名字"` 和 `git config --global user.email "你的邮箱"`
- GitHub 现在不支持密码认证推送，需要用 **Personal Access Token**（在 GitHub Settings → Developer settings → Personal access tokens 生成）或配置 **SSH key**
- 查看当前远程地址：`git remote -v`
- 如果推错了远程地址，可以改：`git remote set-url origin 新地址`
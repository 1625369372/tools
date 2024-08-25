# Git使用方法

## Git配置

### 查询当前版本

```bash
git --version
```

### 升级Git(homebrew)

```bash
brew update 
brew upgrade git 
```

升级后更新shell配置

```bash
source ~/.zshrc  # 如果使用 zsh  
```

### 安装和卸载

```bash
brew uninstall git  
brew install git
```

更改后更新shell配置

```bash
source ~/.zshrc  # 如果使用 zsh  
```

### 建议修改本地默认分支名


```bash
git config --global init.defaultBranch main
```


---

## 远程仓库配置到本地

### 将当前目录设置为本地仓库

#### 当前目录是空目录

```bash
git clone https://github.com/username/repository.git .
```

#### 当前目录非空

```bash
git init  
git remote add origin https://github.com/1625369372/tools.git  
git fetch origin  
git checkout -b main --track origin/main  
git pull
```


### 将当前目录的子目录设置为本地仓库

```bash
git clone https://github.com/username/repository.git
```

### Check Status

```bash
git status
```

---
## 日常使用流程

### 1. 查询当前状态

Before any operation, review your changes:
```bash
git status
```

### 2. 提交更改到暂存区

Stage the changes you want to commit:
```bash
git add <filename>  # Add specific file   
```
or
```bash
git add .           # Add all changes
```

### 3. 将暂存的更改提交到本地仓库

Commit staged changes to your local repository:
```bash
git commit -m "Describe your changes"  
```

### 4. 将本地仓库提交到远程仓库

Push your local commits to GitHub:
```bash
git push origin <branch-name>  
```

Typically, the main branch is named `main` or `master`.

## 分支控制

### Pull remote changes

If there are changes made by others in the remote repository, pull them:
```bash
git pull origin <branch-name>  
```

### Create and switch branches

To develop new features without affecting the main branch, create a new branch:
```bash
git branch <new-branch-name>     # Create new branch   
git checkout <branch-name>       # Switch to specified branch   
git checkout -b <new-branch-name> # Create and switch to new branch
```

### Merge branches

When you've completed a new feature and want to merge it into the main branch:
```bash
git checkout main                # Switch to main branch   
git merge <branch-to-merge>      # Merge branch`  
```

## 清除当前文件的所有git配置和环境

```bash
rm -rf .git
rm -f .gitignore
rm -f .gitattributes
rm -f .gitmodules
rm -f .gitlfs
```

## 更改远程数据源

```bash
# 查看当前远程仓库  
git remote -v  

# 删除名为 "origin" 的远程仓库  
git remote remove origin  

# 添加新的远程仓库  
git remote add origin https://github.com/username/repository.git  

# 验证更改  
git remote -v
```

## .gitignore

在你的项目根目录创建一个 .gitignore 文件（如果还没有的话）：


```bash
touch .gitignore  
```


编辑 .gitignore 文件，添加 .DS_Store：


```bash
echo ".DS_Store" >> .gitignore 
```
 

如果你想在所有文件夹中忽略 .DS_Store 文件，可以这样写：


```bash
echo "**/.DS_Store" >> .gitignore
```


##  查看提交历史

```bash
git log  
```

## 恢复到旧版本

To go back to a previous version:
```bash
git reset --hard <commit-hash>  
```




# Homebrew安装和使用指南

## 验证 Homebrew

验证 Homebrew 是否安装:

在终端中输入:
   ```
   brew --version
   ```
   
   如果 Homebrew 已安装，这个命令会显示 Homebrew 的版本信息。
   如果没有安装，你会看到一个错误消息，说明 "brew" 命令未找到。

更新 Homebrew:

   一般在操作时会先让homebrew升级到最新的版本
   ```
   brew update
   ```
   
## 安装和配置Homebrew

要安装Homebrew首先要安装Xcode Command Line Tools

### Xcode Command Line Tools

#### 验证Xcode Command Line Tools

```bash
xcode-select --version
```

#### 安装 Xcode Command Line Tools:

自动安装（推荐）：  打开终端，运行以下命令：

```bash
xcode-select --install  
```

这会弹出一个窗口，点击"安装"即可。
验证安装是否成功：
```bash
xcode-select --version
```

### 安装homebrew

以下是安装和配置 Homebrew 的详细步骤：

1. 安装 Homebrew：

   打开终端，运行以下命令：
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```
   这个脚本会解释它将做什么，然后暂停，等待你确认。

2. 配置 Homebrew：

   安装完成后，你需要将 Homebrew 添加到你的 PATH 中。根据你使用的 shell，执行以下相应的命令：

   对于 Zsh（macOS Catalina 及以后版本的默认 shell）：
   ```
   echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
   eval "$(/opt/homebrew/bin/brew shellenv)"
   ```

3. 验证安装：

运行以下命令来确认 Homebrew 已正确安装：
   ```
   brew --version
   ```

4. 更新 Homebrew：

安装后立即更新 Homebrew 是个好习惯：
   ```
   brew update
   ```

## 配置

### 配置自动更新（可选）

   你可以设置 Homebrew 在每次使用前自动更新。在你的 shell 配置文件（如 ~/.zshrc 或 ~/.bashrc）中添加：

```bash
export HOMEBREW_AUTO_UPDATE_SECS=86400 # 设置为每天更新一次
```

### 配置自动清理（可选）

设置 Homebrew 自动清理旧版本：
   ```
   export HOMEBREW_INSTALL_CLEANUP=1
   ```

### 保持Homebrew及Homebrew安装的包的更新

定期运行以下命令来保持 Homebrew 和已安装的包为最新版本：

```bash
brew update && brew upgrade && brew cleanup
```


# 环境配置

## 安装

1. 安装Homebrew（如果尚未安装）:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

2. 更新Homebrew:

```bash
brew update
```

3. 安装JDK:

安装最新版本：

```bash
brew install openjdk
```

安装特定版本（例如JDK 11或8）：

```bash
brew install openjdk@11
# 或
brew install openjdk@8
```

4. 链接JDK:

首先创建必要的目录

```bash
sudo mkdir -p /Library/Java/JavaVirtualMachines/
```

链接最新版本：

```bash
sudo ln -sfn /usr/local/opt/openjdk/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk.jdk
```

链接特定版本（例如JDK 21）：

```bash
sudo ln -sfn /usr/local/opt/openjdk@11/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk-21.jdk
```

5. 设置JAVA_HOME环境变量:

打开你的shell配置文件（~/.zshrc），添加以下行：

```bash
nano ~/.zshrc
```

对于最新版本：

```bash
export JAVA_HOME=$(/usr/libexec/java_home)
export PATH=$JAVA_HOME/bin:$PATH
```

对于特定版本（例如JDK 21）：

```bash
export JAVA_HOME=$(/usr/libexec/java_home -v 21)
export PATH=$JAVA_HOME/bin:$PATH
```

6. 使更改生效:

```bash
source ~/.zshrc  
```

7. 验证安装:

```bash
java -version
javac -version
```

8. 管理多个Java版本:

如果安装了多个版本，可以使用以下命令切换：

```bash
export JAVA_HOME=$(/usr/libexec/java_home -v 11)  # 切换到Java 11
# 或
export JAVA_HOME=$(/usr/libexec/java_home -v 1.8)  # 切换到Java 8
```

9. 更新JDK:

定期运行以下命令来更新JDK：

```bash
brew update
brew upgrade openjdk  # 更新最新版本
# 或
brew upgrade openjdk@11  # 更新特定版本
```

## 卸载

1. 卸载JDK

卸载非特定版本（最新版本）：

```bash
brew uninstall openjdk
```

卸载特定版本（例如JDK 21）：

```bash
brew uninstall openjdk@11
```

2. 移除符号链接

对于非特定版本（最新版本）：

```bash
sudo rm -rf /Library/Java/JavaVirtualMachines/openjdk.jdk  
```

对于特定版本（例如JDK 21）：

```bash
sudo rm -rf /Library/Java/JavaVirtualMachines/openjdk-21.jdk   
```

3. 清理Homebrew缓存

```bash
brew cleanup
```

4. 移除环境变量设置

编辑你的shell配置文件（~/.bash_profile 或 ~/.zshrc），删除或注释掉以下行：

```bash
export JAVA_HOME=$(/usr/libexec/java_home)
export PATH=$JAVA_HOME/bin:$PATH
```

如果你为特定版本设置了JAVA_HOME，也要删除或注释掉这些行，例如：

```bash
export JAVA_HOME=$(/usr/libexec/java_home -v 21)
```

5. 重新加载shell配置

```bash
source ~/.zshrc  # 如果使用zsh
```

6. 验证卸载

运行以下命令，确保Java已被卸载：

```bash
java -version
javac -version
```

这些命令应该返回"command not found"错误。

7. 清理系统Java缓存（可选）

```bash
sudo rm -rf /Library/Internet\ Plug-Ins/JavaAppletPlugin.plugin
sudo rm -rf /Library/PreferencePanes/JavaControlPanel.prefPane
```

8. 检查并删除任何剩余的Java相关文件（可选）

```bash
sudo rm -rf /Library/Java
sudo rm -rf ~/Library/Application\ Support/Oracle/Java
```

9. 如果你安装了多个版本，重复步骤1-3为每个版本执行卸载操作

完成这些步骤后，你应该已经成功卸载了JDK并移除了所有相关配置。请注意，这些步骤会完全移除JDK，如果你之后需要使用Java，你需要重新安装。

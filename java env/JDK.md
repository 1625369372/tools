# JDK环境配置

## MAC上安装JDK

<u>需要安装homebrew</u>

### 安装和配置

运行以下命令来安装最新版本的OpenJDK：

```bash
brew update 
brew install openjdk@22
```

安装完成后，您需要链接这个版本的Java，使其成为系统默认版本：

```bash
sudo ln -sfn $(brew --prefix)/opt/openjdk/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk.jdk
```

将Java路径添加到shell配置文件中，使用zsh编辑~/.zshrc文件。添加以下行：

```bash
export PATH="/opt/homebrew/opt/openjdk/bin:$PATH" 
```

  重新加载配置文件：

```bash
source ~/.zshrc
```

### 验证版本

```bash
java -version
```

### 查询已安装的所有版本

系统中所有版本：
```bash
/usr/libexec/java_home -V
```

查看使用homebrew安装的版本：

```bash
brew list --versions java
```
（特定版本）

```bash
brew list --versions openjdk@17
```


### 升级到最新版

```bash
brew upgrade openjdk
```

### 删除旧版本


```bash
brew uninstall openjdk@17
brew cleanup
```

注意要先删除jenv版本，再删除jdk

### 安装和配置特定版本的Java

<span style="background:#d3f8b6"><u>eg. Java17</u></span>

使用 Homebrew 安装特定版本的 JDK：

```bash
brew install openjdk@17  
```


安装完成后，Homebrew 会显示一些信息，包括 JDK 的安装路径。通常，它会在 `/opt/homebrew/opt/openjdk@17` 目录下。

创建一个符号链接，使系统能够找到这个 Java 版本（这步可选，但建议执行）：

```bash
sudo ln -sfn /opt/homebrew/opt/openjdk@17/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk-17.jdk
```

---

## 使用`jenv`的Java版本管理

### 注意事项

- 每次安装新的 Java 版本后，都要记得用 `jenv add` 添加到 jenv。
- 在项目根目录使用 `jenv local` 设置项目特定的 Java 版本是个好习惯。
- 使用 `jenv doctor` 命令可以诊断常见的配置问题。


### `jenv`的安装和配置

安装 `jenv`：

```bash
brew install jenv
```

配置 shell：
   将以下行添加到你的 shell 配置文件中：
   
   ```bash
   export PATH="$HOME/.jenv/bin:$PATH"
   eval "$(jenv init -)"
   ```

   然后重新加载配置文件：
   
   ```bash
   source ~/.zshrc  # 或 source ~/.bash_profile
   ```

添加 Java 版本到 `jenv`：
   对于每个你想管理的 Java 版本，运行以下命令：

```bash
jenv add /Library/Java/JavaVirtualMachines/openjdk-17.jdk/Contents/Home
```

   注意：路径可能因 Java 版本和安装方式而异。如果是用 Homebrew 安装的，路径通常是：
   ```bash
   jenv add /opt/homebrew/opt/openjdk@17
   ```

4. 查看已添加的版本：

```bash
jenv versions
```

5. 设置全局 Java 版本：

```bash
jenv global 17.0
```

### 查询`jenv`当前版本和所有可用版本


```bash
jenv versions
```

如果不知道system是什么版本可以使用
```bash
/usr/libexec/java_home -V
```
查询系统默认的

### 将所有新版本/特定版本JDK添加到`jenv`

所有版本
```bash
jenv add $(/usr/libexec/java_home)
```

or

指定版本（<u>建议，不然会添加一堆重复的</u>）
```bash
jenv add /opt/homebrew/opt/openjdk@17
# or jenv add /opt/homebrew/opt/openjdk@17/libexec/openjdk.jdk/Contents/Home
```

添加后验证


```bash
jenv versions
```


### 更新 `jenv` 的可用 Java 版本：

如果你安装了新的 Java 版本，需要刷新 jenv：

```bash
jenv refresh-versions
```

### 更新全局默认Java版本

```bash
jenv global 22.0.2 # or jenv global system 更改为系统默认
```

设置后需要刷新和验证


```bash
jenv rehash
java -version
```


### 更新后重新配置和加载

删除了旧版本的jdk和jenv之后刷新配置：
```bash
jenv rehash

export PATH="$HOME/.jenv/bin:$PATH"  
eval "$(jenv init -)"
source ~/.zshrc  # 或 source ~/.bash_profile
```

### 更改后检查Java版本、`jenv`和JAVA_HOME是否全部一致


```bash
java -version  
echo $JAVA_HOME  
jenv versions
```


### 删除一个 Java 版本：

如果你不再需要某个版本，可以这样删除：

```bash
jenv remove 11.0
```

注意要先删除jenv版本，再删除jdk

### 更新特定目录 Java 版本：

   进入项目目录，然后运行：

```bash
jenv local 11.0
```
   这会在当前目录创建一个 .java-version 文件。

### 更新特定 shell 会话的 Java 版本：

```bash
jenv shell 17.0
```

8. 验证当前使用的 Java 版本：

```bash
java -version
```

### 使用`jenv`自动设置和更新JAVA_MOME



### 使用 `jenv` 管理 Maven 或 Gradle：

如果你使用 Maven 或 Gradle，可以启用相应的插件：

```bash
jenv enable-plugin maven
jenv enable-plugin gradle
```


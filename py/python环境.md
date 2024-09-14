## 安装

1. 更新Homebrew：

```bash
brew update
```

2. 安装Python：

```bash
brew install python  
```

这会安装最新版本的Python 3。

3. 验证安装：

```bash
python3 --version   
pip3 --version 
```

4. 设置Python路径：  

打开终端。使用nano打开.zshrc文件：

```bash
nano ~/.zshrc  
```

使用箭头键导航到文件末尾，添加以下行：

```bash
export PATH="/usr/local/opt/python/libexec/bin:$PATH"  
```

完成编辑后，按 Ctrl + X保存并退出nano；当提示"Save modified buffer?"时，按 Y 确认保存；之后按 Enter 确认文件名

重新加载.zshrc文件以使更改生效：

```bash
source ~/.zshrc
```

## 升级

非常好，我会根据你使用zsh的情况重新组织这些步骤。以下是优化后的流程：

1. 更新Homebrew
```zsh
brew update
```

2. 升级Python
```zsh
brew upgrade python
```

3. 验证升级
```zsh
python3 --version
```

4. 查询Python路径
```zsh
which python3
```

5. 编辑zsh配置文件
```zsh
nano ~/.zshrc
```

6. 在nano编辑器中，检查并修改PATH
查找包含 `PATH` 的行。如果需要添加Python路径，在文件中合适地方添加：
```zsh
export PATH="/usr/local/opt/python/libexec/bin:$PATH"
```
确保使用 `which python3` 命令得到的实际路径。

例如，如果 `which python3` 显示 `/opt/homebrew/bin/python3`，你可能需要添加：`export PATH="/opt/homebrew/bin:$PATH"`

7. 保存并退出nano
- 按 `Ctrl + X`
- 按 `Y` 确认保存
- 按 `Enter` 确认文件名

8. 重新加载zsh配置
```zsh
source ~/.zshrc
```

9. 更新pip
```zsh
pip3 install --upgrade pip
```

10. 清理旧版本Python（可选）
```zsh
brew cleanup python
```

11. 验证PATH更新
```zsh
echo $PATH
```
确保新的Python路径出现在输出的开头。

12. 再次验证Python版本
```zsh
python3 --version
```


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



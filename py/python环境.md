## python环境配置

使用homebrew安装python

```bash
brew install python
```

验证安装：

```bash
python3 --version  
pip3 --version
```

更新 Python 和相关工具：

```bash
brew update && brew upgrade python
```

设置 PYTHONPATH（如果需要）：  
在 shell 配置文件中添加：

```bash
export PYTHONPATH="/path/to/your/python/modules:$PYTHONPATH"  
```

## 安装&配置

访问[Anaconda 官网](https://www.anaconda.com/products/distributionhttps://www.anaconda.com/products/distribution)
下载 Mac OS 版本的安装程序（选择图形化安装程序）
双击下载的 .pkg 文件，按照安装向导的指示完成安装

安装完成后，打开终端，执行以下步骤：

a. 查找Anaconda安装路径：

```bash
which anaconda  
```

这会显示类似 `/Users/YOUR_USERNAME/anaconda3/bin/conda` 的路径

b. 使用nano编辑你的zsh配置文件：

```bash
nano ~/.zshrc  
```

c. 在打开的文件中，添加以下行（根据实际路径调整）：

```java
export PATH="/opt/anaconda3/bin:$PATH"
```

例如Anaconda 的安装路径是：
```bash
/opt/anaconda3/bin/anaconda 
```
则添加以下行：
```bash
export PATH="/opt/anaconda3/bin:$PATH"
```


d. 保存并退出nano：

按 Ctrl + X
按 Y 确认保存
按 Enter 确认文件名

e. 重新加载配置：

```bash
source ~/.zshrc  
```

验证安装:

```bash
conda --version
```

## iCloud符号链接

当然，我很乐意为你详细解释创建符号链接的完整过程。这个方法可以让你更方便地在 Jupyter Lab 中访问 iCloud 文件夹。以下是详细的步骤：

1. 确认 iCloud Drive 位置
   在终端中输入以下命令来确认你的 iCloud Drive 位置：
   ```zsh
   ls ~/Library/Mobile\ Documents/com~apple~CloudDocs/
   ```
   如果这个命令显示了你的 iCloud 文件和文件夹，那么路径是正确的。

2. 创建符号链接
   在终端中输入以下命令：
   ```zsh
   ln -s ~/Library/Mobile\ Documents/com~apple~CloudDocs/ ~/iCloud
   ```
   这个命令的含义是：
   - `ln -s`: 创建一个符号链接
   - `~/Library/Mobile\ Documents/com~apple~CloudDocs/`: 源目录（你的 iCloud Drive 位置）
   - `~/iCloud`: 目标位置（在你的主目录下创建一个名为 "iCloud" 的链接）

3. 确认符号链接创建成功
   输入以下命令来确认链接已经创建：
   ```zsh
   ls -l ~/iCloud
   ```
   你应该能看到 iCloud 文件夹的内容。

4. 在 Finder 中查看（可选）
   如果你想在 Finder 中查看这个新创建的链接：
   - 打开 Finder
   - 按 `Cmd + Shift + H` 快捷键跳转到你的主目录
   - 你应该能看到一个名为 "iCloud" 的文件夹图标

5. 在 Jupyter Lab 中使用
   - 打开 Jupyter Lab（如果还没有打开的话）
   - 在文件浏览器中，你现在应该能在你的主目录下看到 "iCloud" 文件夹
   - 点击这个文件夹就可以访问你的 iCloud Drive 内容了

6. 删除符号链接（如果将来需要的话）
   如果你以后想删除这个符号链接，可以在终端中输入：
   ```zsh
   rm ~/iCloud
   ```
   注意：这只会删除链接，不会影响实际的 iCloud 文件夹内容。

注意事项：
- 创建符号链接不会影响原始文件夹的内容或位置。
- 如果你的 iCloud Drive 位置与上述不同，请相应地调整命令中的路径。
- 确保你有足够的权限来创建符号链接和访问 iCloud 文件夹。
- 在 Jupyter Lab 中使用 iCloud 文件时要小心，因为更改会同步到所有连接的设备。

## jupyter lab

### 配置 Python 3 笔记环境

1. 创建 Python 3 虚拟环境
   打开终端，输入以下命令：
   ```zsh
conda create -n python_notes python=system ipykernel
   ```
   这会创建一个名为 "python_notes" 的环境，使用homebrew配置的 Python 版本。

2. 激活新环境
   ```zsh
   conda activate python_notes
   ```

3. 安装常用的数据科学包
   ```zsh
   conda install numpy pandas matplotlib seaborn scikit-learn jupyter
   ```

4. 将环境添加到 Jupyter
   ```zsh
   python -m ipykernel install --user --name python_notes --display-name "Python (Notes)"
   ```

5. 在 iCloud 中创建 Python 笔记文件夹
   ```zsh
   mkdir ~/iCloud/Python_Notes
   ```

6. 验证 Python 版本和安装的包
   ```zsh
   python --version
   conda list
   ```

7. 启动 Jupyter Notebook（可选）
   ```zsh
   jupyter notebook --notebook-dir=~/iCloud/Python_Notes
   ```

这些修改的优点：
- 使用 `python` 而不是特定版本号，确保安装最新的稳定版本。
- 环境名称改为 "python_notes"，更加通用。
- Jupyter 内核显示名称改为 "Python (Notes)"，不指定具体版本号。
- 添加了验证步骤，以确认安装的 Python 版本和包。

#### 更新

更新 Homebrew 的 Python：

```zsh
brew update   
brew upgrade python 
```
 
b. 更新 Conda 环境：

```zsh
conda activate python_notes   
conda update --all  
```

c. 重新安装 ipykernel：

```zsh
conda install --force-reinstall ipykernel   
python -m ipykernel install --user --name python_notes --display-name "Python (Notes)"  
```

验证更新

```zsh
python --version  
conda list
```


## 删除环境

### 步骤一：确保环境已被停用

以 `notes` 环境为例

首先，确认您当前是否在 `notes` 环境中。如果是，需要先停用该环境。

**在终端中输入：**

`conda deactivate`  

这将使您退出当前的 Conda 环境，回到 base 环境或未激活的状态。您的终端提示符应该不再显示 `(notes)`。

---

### **步骤二：删除 `notes` 环境**

使用以下命令删除名为 `notes` 的 Conda 环境：

`conda env remove -n notes`  

**参数说明：**

- `conda env remove`：这是删除 Conda 环境的命令。
- `-n notes`：指定要删除的环境名称为 `notes`。

**完整输出示例：**

`(base) user@computer ~ % conda env remove -n notes   Remove all packages in environment /Users/your_username/opt/anaconda3/envs/notes:    ## Package Plan ##      environment location: /Users/your_username/opt/anaconda3/envs/notes    Proceed ([y]/n)? y    Removing specific packages...   ...`  

---

### **步骤三：验证环境是否已被删除**

您可以列出当前所有的 Conda 环境，确认 `notes` 已被删除。

**在终端中输入：**

`conda env list`  

输出的环境列表中，应该不再包含 `notes` 环境。例如：

`(base) user@computer ~ % conda env list   # conda environments:   #   base                  *  /Users/your_username/opt/anaconda3`  

---

### **步骤四：删除残留文件（可选）**

有时，删除环境后可能会有一些残留文件，您可以手动检查并删除：

1. **检查 Conda 环境目录：**
    
    默认情况下，Conda 环境存储在 `~/opt/anaconda3/envs/` 或 `~/miniconda3/envs/` 目录下。
    
2. **删除 `notes` 环境目录（如果仍存在）：**
    
    `rm -rf ~/opt/anaconda3/envs/notes`  
    
    **注意：**请谨慎使用 `rm -rf` 命令，确保路径正确，以免误删其他文件。
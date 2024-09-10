



# Node.js 

## node.js && npm

1. Install Node.js using Homebrew:

```bash
brew install node
```

2. Verify the installation:

```bash
node --version
npm --version
```

3. Update Node.js to the latest version:

```bash
brew upgrade node
```

4. Install a specific version of Node.js:

```bash
brew install node@14
```

5. Switch between Node.js versions:

```bash
brew unlink node
brew link --force node@14
```

6. Update npm to the latest version:

```bash
npm install -g npm@latest
```

7. Install common global packages (optional):

```bash
npm install -g yarn
npm install -g typescript
```

8. Switch npm registry (if needed):

```bash
# Set to official registry
npm config set registry https://registry.npmjs.org/

# Or set to Taobao mirror (if in China)
npm config set registry https://registry.npmmirror.com/
```

9. Uninstall Node.js:

```bash
brew uninstall node
```

10. Clean up Homebrew cache:

```bash
brew cleanup
```

Note: When using Homebrew to manage Node.js, you can only have one version active at a time. If you need to frequently switch between multiple Node.js versions, consider using a version manager like nvm.

## Vue CLI

安装 Vue CLI：

Vue CLI 是 Vue.js 开发的标准工具，它简化了 Vue.js 项目的搭建过程。使用 npm 全局安装 Vue CLI：


```bash
npm install -g @vue/cli  
```


安装完成后，验证安装：


```bash
vue --version
```

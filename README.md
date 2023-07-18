<!-- ---
html:
  embed_local_images: false
  embed_svg: true
  offline: false
  toc: true

print_background: false
---

# 测试

## 这是一个测试

总所周知，git 是一个很好用的版本控制工具，比 SVN 好用很多

### 你好

大家好啊

### 世界

开源精神

### 这是一个属于 Java 的世界

code changes the world -->


<h1 align="center">如何为一个仓库部署 GitHub Pages ？</h1>

### 0. 开发环境

- Visual Studio Code（因为有 MarkDown 插件 `MPE`，支持 MarkDown 导出网页支持的 HTML）

### 1. 个人博客搭建

1. 本人建议直接开辟一个新仓库，公有（public）并且仓库名称为 `自己的用户名.github.io`，直接创建一个空仓库

2. 在自己的电脑上克隆这个仓库，这时你的本地 IDE 应该一个文件都没有（`.git` 有但编辑不了）

3. 你的默认工作分支是 `main` 分支，这里直接写一个 `README.md` 文件，注意要在 MarkDown 文件中配置一下 `html` 的相关配置 [相关链接可以看这里](https://shd101wyy.github.io/markdown-preview-enhanced/#/zh-cn/html?id=%e4%bf%9d%e5%ad%98%e6%97%b6%e8%87%aa%e5%8a%a8%e5%af%bc%e5%87%ba)

```markdown
---
html:
  embed_local_images: false
  embed_svg: true
  offline: false
  toc: undefined

print_background: false
---
```
这个 **必须要配置**，否则导出的 `html` 页面不能被 GitHub Pages 识别渲染，造成部署失败（多次踩坑 QAQ）

4. 生成的文件为 `README.html`，直接把 `README.md` 删了，并将 `README.html` 改为 `index.html`，这时只保留一个 `index.html` 文件

5. 前置工作装备完毕，代码推送

```bash
git add .
git commit -m "Init: First init" .
git push origin main
```

6. 回到 GitHub 仓库，在 Settings 里点击 pages，Branch 选择 main 就行，`/(root)` 文件说明 `index.html` 必须放在根目录（ `/docs` 有时候适用于下面的开源项目搭建 ）直接 `save` 保存

7. 出现 `visit` 小按钮，点击即可访问

### 2. 开源项目搭建

#### 原分支搭建

在原分支搭建我不太推荐，因为原分支是自己项目的代码，装进去一个 `docs` 目录不太美观（代码洁癖就是了）。

如果你想要真的把网站代码放在项目分支上的话，那就新建一个文件夹 `docs`，用于存放网站文件，**并且在上面提到的 `pages` 里把 `/(root)` 修改为 `/docs`，否则不生效**

#### 新开 gh-pages 分支搭建

直接在 **GitHub 仓库** 和 **自己的 IDE** 创建一个分支 `gh-pages`，创建 `index.html` 操作和上面一样，推送成功后在 `Setting` 里把 `Branch` 里的分支选择为 `gh-pages`，其他保持一致即可


### 3. 补充

这里只是实现了一锤子买卖，没有 `css` 等美化，只有纯 MarkDown 生成的 HTML 文件，需要美化的话可以去参考 `Hexo` 或者 `Hugo` 的板子，配置过程原理相同，布置好都是基于 `GitHub Pages` 的，希望小伙伴可以触类旁通，有问题谷歌百度后可以提 **Issue**
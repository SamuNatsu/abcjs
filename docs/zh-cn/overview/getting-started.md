# 入门指南

## 你应该使用哪种版本？

### node.js

如果你处于 Node 生态系统中，只需通过以下命令安装打包版本：

```
npm install --save abcjs
```

要导入库，请使用：

```
import abcjs from "abcjs";
```

要导入音频控件的样式，请使用：

```
import 'abcjs/abcjs-audio.css';
```

### 旧式最小化下载

如果你在网站上编写了大量的 JavaScript，并且你自己生成音乐，或者允许用户使用 ABC 记谱法输入音乐（无论是整首曲子还是片段），那么你可能希望使用`abcjs-basic`。这将使你在更小的包中控制生成过程。

如果你的页面上已经有 ABC 记谱法，并且不想对页面进行过多修改，那么你可以使用 `abcjs-plugin`，它会在页面加载时渲染页面上找到的所有 ABC 记谱法，只需包含一行脚本即可。另一个用途是，如果你的博客有一个评论区，那么你可以允许用户发布 ABC 曲目，它们会自动以乐谱形式显示。

如果你正在查看别人的网站并看到页面上的 ABC 记谱法，想要查看其标准记谱法的样子，可以在 FireFox 或 Chrome 中安装 Greasemonkey 脚本，它会为你渲染 ABC 记谱法。

以下是最新版本。你可以直接下载其中一个：

- [Basic](https://raw.githubusercontent.com/paulrosen/abcjs/main/dist/abcjs-basic-min.js)

- [Plugin](https://raw.githubusercontent.com/paulrosen/abcjs/main/dist/abcjs-plugin-min.js)

- [音频控件样式](https://raw.githubusercontent.com/paulrosen/abcjs/main/abcjs-audio.css)

**注意：不要直接链接这些文件！请将它们上传到你自己的服务器！[原因在此](https://github.com/blog/1482-heads-up-nosniff-header-support-coming-to-chrome-and-firefox)**

你也可以使用 CDN: `https://cdn.jsdelivr.net/npm/abcjs@VERSION/dist/abcjs-basic-min.js`，其中 `VERSION` 是你想使用的库版本。请注意，我不维护这些文件，因此不能保证将来仍然可用。

当直接加载库时，你会在 `window.ABCJS` 中找到该库。

## 最简单的用法

```html
<div id="paper"></div>
```

```javascript
abcjs.renderAbc("paper", "X:1\nK:D\nDD AA|BBA2|\n");
```

<render-abc :abc="`X:1\nK:D\nDD AA|BBA2|\n`"></render-abc>

# 入门指南

## 版本选择

### node.js

如果你使用 Node 生态，只需通过以下命令安装打包版本：

```sh
npm install --save abcjs
```

要引入库，请使用：

```js
import abcjs from "abcjs";
```

要引入音频控件样式，请使用：

```js
import 'abcjs/abcjs-audio.css';
```

### 旧式单文件库引入

如果你在网站上编写了大量的 JavaScript 且要求自行生成乐谱，或者允许用户使用 ABC 记谱法输入乐谱（无论是整首曲子还是片段），那么你可能希望使用`abcjs-basic`。

如果你的页面上已经有 ABC 记谱法，并且不想对页面进行过多修改，那么你可以使用 `abcjs-plugin`，它会在页面加载时渲染页面上找到的所有 ABC 记谱法，只需包含一行脚本即可。它的另一个用途是，如果你的博客有一个评论区，那么你可以允许用户发布 ABC 曲目，它们会自动以乐谱形式显示。

如果你正在查看别人的网站并看到页面上的 ABC 记谱法，且想要查看其渲染出来的乐谱，可以在 FireFox 或 Chrome 中安装 Greasemonkey 脚本，它会为你渲染 ABC 记谱法。

以下是最新版本，你可以直接下载其中一个：

- [abcjs-basic-min.js](https://raw.githubusercontent.com/paulrosen/abcjs/main/dist/abcjs-basic-min.js)
- [abcjs-plugin-min.js](https://raw.githubusercontent.com/paulrosen/abcjs/main/dist/abcjs-plugin-min.js)
- [abcjs-audio.css](https://raw.githubusercontent.com/paulrosen/abcjs/main/abcjs-audio.css)

**注意：不要直接链接这些文件！请将它们上传到你自己的服务器！[原因在此](https://github.com/blog/1482-heads-up-nosniff-header-support-coming-to-chrome-and-firefox)**

你也可以使用 CDN: `https://cdn.jsdelivr.net/npm/abcjs@VERSION/dist/abcjs-basic-min.js`，其中 `VERSION` 是你想使用的库版本。请注意，我不维护这些文件，因此不能保证将来仍然可用。

当直接加载库时，你会在 `window.ABCJS` 中找到该库。

## 最简单用法

```html
<div id="paper"></div>
```

```javascript
abcjs.renderAbc("paper", "X:1\nK:D\nDD AA|BBA2|\n");
```

<render-abc :abc="`X:1\nK:D\nDD AA|BBA2|\n`"></render-abc>

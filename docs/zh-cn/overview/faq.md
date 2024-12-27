# 常见问题

## 如何创建播放小组件？

请参阅 [沙箱](../audio/synthesizer-sandbox.md)。您可以根据需要定制音频控件。

## 我需要包含哪些脚本？

### 对于 Node.js：

```bash
npm install abcjs --save-dev
```

```javascript
import abcjs from "abcjs";
```

### 对于普通 JavaScript：

将文件 `dist/abcjs-basic-min.js` 下载到您的项目中。然后在顶部添加：

```javascript
<script src="js/abcjs-basic-min.js" type="text/javascript"></script>
```

## 如何在我的 ABCJS 项目中使用我本地保存的音色库？

请参阅 [沙箱](../audio/synthesizer-sandbox.md) 以查看语法。

## 我试图在点击时获取音符的名称，但不起作用。我有一个乐谱的可视化渲染，但是没有播放小组件。

可以在乐谱结构中添加一些可选的额外信息。这些信息是在创建合成器时添加的，但由于并非所有用户都需要它，因此默认情况下不会添加，以避免不必要的代码执行。

要添加该信息：

```javascript
var visualObj = abcjs.renderAbc( ... )
visualObj[0].setUpAudio()
```

## 我可以在 React Native / 其他移动开发框架中使用 ABCJS 吗？

ABCJS 需要一个 DOM 来 1) 计算渲染后音符将占用的空间，以及 2) 使用 SVG 渲染音符。这使得将 ABCJS 与不使用 DOM 的框架（如 React Native）集成变得不那么直接。

一个来自 Matthew Dorner 的方法：他的应用程序 react-native-songbook 依赖于 react-native-svg（通过 standalone-vexflow-context）来绘制到 SVG 上。您也可以尝试在 React Native webview 组件中渲染 ABCJS 元素，该组件提供了所需的 DOM，就像浏览器访问具有 ABCJS 功能的外部页面一样，而不是作为原生渲染引擎。感谢 @rpattcorner 提供的这个小贴士。

## 如何在我的服务器端渲染应用中使用 ABCJS？

如果您正在使用 Nuxt、Next 或任何其他在发送给客户端之前在服务器上构建页面的框架，则必须推迟调用 abcjs 直到进入客户端环境。

这里有一个示例：

```javascript
const abcjs = process.browser ? require('abcjs') : null;

if (abcjs) {
	abcjs.renderAbc( ... )
}
```

## 为什么我必须等到用户与页面交互后才能创建音频？

因为浏览器对 AudioContext 施加了限制，以防止开发者构建在页面加载时自动播放声音的网站，所以在用户对页面进行某些操作之前，你无法开始缓冲音频。

## 如何让音频立即开始播放？

有些网络传输和声音缓冲区的构建需要花费一些时间。这部分工作可以稍微提前完成，因此，一旦用户与页面进行了交互，并且你知道想要播放什么音乐时，就可以开始这个过程了。你会注意到 `init()` 和 `prime()` 调用会返回一个 `Promise`。当这些 `Promise` resolve 后，点击 `play()` 将会非常快。

## 如何避免这种错误：“The AudioContext was not allowed to start. It must be resumed (or created) after a user gesture on the page.”

不要在用户与页面互动之前调用任何与音频相关的功能。

## 我想用自定义的符号/图标替换所有的音符。我该怎么做？

在调用 `renderAbc()` 之后，查找所有具有“abcjs-note”类的元素，并将其中的路径替换成你的图片。
为了实现这一点，请使用参数 `{ add_classes: true }` 来调用 `renderAbc`。请注意，还有其他可以搜索的内容，比如音符的五线谱线条，这样你可以为不同的音符设置不同的图片。

## 如何调整音符的水平位置？例如，如果我希望音符能够水平居中？

你可以使用 `%%staffwidth 400` 来选择五线谱所占用的像素数。你可以通过测试这个值来达到满意的效果。还可以使用 `%%stretchlast` 来拉伸最后一行乐谱。此外，`staffwidth` 也可以作为参数传递给 `renderAbc` 函数。更多示例请参考 wrap.html 演示文件。

## 我在转调我的曲子时遇到了困难

可视化上的转调和音频上的转调是分开处理的，以适应那些可能希望乐谱被转调但不希望音频回放也转调的情况，反之亦然。关于如何处理这两种形式的转调，请参阅 basic-transpose.html 和 editor-transpose.html 示例。

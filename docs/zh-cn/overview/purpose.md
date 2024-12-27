# 宗旨

该库使您能够轻松地将 **乐谱** 融入到您的 **网站** 中。它主要面向 **JavaScript 开发人员**。不过，对于简单使用来说，所需的 JavaScript 代码量非常小，因此您不需要成为一名专家。

## 用途

* 绘制任意乐谱
* 即时修改乐谱
* 对绘制的乐谱进行动画效果处理
* 使用 CSS 样式化乐谱
* 为乐谱创建合成音频
* 在网页上搜索 **ABC** 格式的字符串（例如在博客文章或评论中）并将其转换成乐谱
* 允许用户通过输入 **ABC** 字符串即时修改乐谱

## 它不适用于

* 它不提供可视化编辑器（尽管如果您想编写一个，可以将其作为基础使用）

## 无需编程的开源应用

* 如果您只是想渲染您的 abc 但不是制作一整个网站，有许多公开可用的应用程序可供使用
* 若要在浏览器中处理乐谱，请参阅 [abcjs: Quick Editor](https://editor.drawthedots.com)
* 另请参阅 Michael Eskin 的 [ABC 工具](https://michaeleskin.com/abctools/abctools.html)，这是一个功能更全面的编辑器
* 如果您使用 VSCode，可以安装一个扩展。按 shift-cmd-X 进入扩展面板，然后搜索“abcjs”。安装后，您可以在文件中键入时看到对乐谱的渲染。要使用它，请打开您的乐谱文件（以`.abc`结尾），然后按 shift-cmd-P 打开命令面板。搜索“abcjs”以打开预览窗格。

## 浏览器/设备支持

* 该库的可视化部分支持 IE9 及更高版本、Safari 5.1 及更高版本以及所有现代浏览器
* 该库的合成音频部分不支持 IE，但在任何支持 `AudioContext.resume` 和 `Promises` 的系统上都能工作。也就是说，任何比 Firefox 40、Safari 9.1、Edge 13 和 Chrome 43 更新的浏览器

## 由 BrowserStack 支持

感谢 [BrowserStack](https://browserstack.com/) 对这个开源项目的支持。

![BrowserStack](https://paulrosen.github.io/abcjs/img/browserstack-logo-600x315.png)

## 许可证

[MIT 许可证](http://opensource.org/licenses/MIT)

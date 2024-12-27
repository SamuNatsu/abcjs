# 用于在浏览器中插入音乐的 JavaScript 库

![abcjs](https://paulrosen.github.io/abcjs/img/abcjs_comp_extended_08.svg)

**ABC 乐谱记法** 是一种仅使用一串字符来指定乐谱的格式。
例如，下面的字符串编码了其下方显示的音乐。该音乐是通过在此网页上包含此库绘制的。

```
X: 1
T: Cooley's
M: 4/4
L: 1/8
K: Emin
|:D2|EB{c}BA B2 EB|~B2 AB dBAG|FDAD BDAD|FDAD dAFD|
EBBA B2 EB|B2 AB defg|afe^c dBAF|DEFD E2:|
|:gf|eB B2 efge|eB B2 gedB|A2 FA DAFA|A2 FA defg|
eB B2 eBgB|eB B2 defg|afe^c dBAF|DEFD E2:|
```

<render-abc ref="tune" :abc="`X: 1
T: Cooley's
M: 4/4
L: 1/8
K: Emin
|:D2|EB{c}BA B2 EB|~B2 AB dBAG|FDAD BDAD|FDAD dAFD|
EBBA B2 EB|B2 AB defg|afe^c dBAF|DEFD E2:|
|:gf|eB B2 efge|eB B2 gedB|A2 FA DAFA|A2 FA defg|
eB B2 eBgB|eB B2 defg|afe^c dBAF|DEFD E2:|`" ></render-abc>

此外，音乐也可以通过合成器播放：

<render-audio :obj="$refs"></render-audio>

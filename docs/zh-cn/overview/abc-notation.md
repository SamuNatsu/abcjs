# ABC 乐谱记法

**abcjs** 的输入主要是标准的 ABC 乐谱记法。该记法在此处描述：

[ABC 乐谱记法](http://abcnotation.com/learn)

标准的工作文档是 [ABC 标准](https://abcnotation.com/wiki/abc:standard)

此外，还有许多非正式的记法，特别是新的 `%%` 指令，这些指令被支持以与其他 ABC 软件兼容。

## 不支持的特性

我们已经尝试与其它 ABC 软件保持兼容，但有一些例外。

有些其他包支持的功能是特定于该包的环境，并不适用于基于 Web 的解决方案。这些功能不受支持。

以下是一些可能不会被支持的格式选项列表：

```
%%abc
%%abc2pscompat
%%abcm2ps
%%autoclef
%%beginps
%%beginsvg
%%bgcolor
%%break
%%breaklimit
%%breakoneoln
%%clip
%%deco
%%decoration
%%eps
%%format
%%fullsvg
%%map
%%micronewps
%%pango
%%pdfmark
%%ps
%%select
%%tune
%%voicemap
```

有些其他包支持的功能我们还没有来得及支持。如果你遇到了希望用到的功能，请告诉我们。

## 对标准的扩展

### 替换音符头

在K:和V:元素中，你可以包含参数：

```
style=rhythm
style=harmonic
style=x
style=normal
style=triangle
```

你也可以将上述内容作为单个音符的装饰，只影响那个音符：

```
!style=rhythm!
```

这会将音符头更改为不同的形状。

这是一个示例：

<show-and-render-abc :abc='`X:1
T:alternate heads
M:C
L:1/8
U:n=!style=normal!
K:C treble style=rhythm
"Am" BBBB B2 B&gt;B | "Dm" B2 B/B/B "C" B4 |\
"Am" B2 nGnB B2 nGnA | "Dm" nDB/B/ nDB/B/ "C" nCB/B/ nCB/B/ |B8| B0 B0 B0 B0 |]
%%text This translates to:
[M:C][K:style=normal]
[A,EAce][A,EAce][A,EAce][A,EAce] [A,EAce]2 [A,EAce]&gt;[A,EAce] |\
[DAdf]2 [DAdf]/[DAdf]/[DAdf] [CEGce]4 |\
[A,EAce]2 GA [A,EAce] GA |\
D[DAdf]/[DAdf]/ D[DAdf]/[DAdf]/ C [CEGce]/[CEGce]/ C[CEGce]/[CEGce]/ |[CEGce]8 | [CEGce]2 [CEGce]2 [CEGce]2 [CEGce]2 |]
GAB2 !style=harmonic![gb]4|GAB2 [K: style=harmonic]gbgb|
[K: style=x]
C/A,/ C/C/E C/zz2|
w:Rock-y did-nt like that
`' ></show-and-render-abc>

### 和弦跳过:

如果你想跳过一个和弦，可以使用以下之一作为和弦：

```
"^break"
"^(break)"
"^no chord"
"^n.c."
"^tacet"
```

<render-abc ref="tune" :abc='`X:1
T:Struttin With Some BBQ
C:1923 Lil Hardin Armstrong
M:4/4
L:1/8
K:F
"G7"d4AFGA|dA-A6|"C7"cB"^N.C."GF EDC=B,|_B,2zF EFAc|
`' ></render-abc>

<render-audio :obj="$refs"></render-audio>

这些是不区分大小写的。

### 标记

要任意地为下一个音符添加类 "mark"，你可以使用装饰：

```
!mark!
```

<render-abc :abc='`X:1
K:C
e!mark!f|g
`' ></render-abc>

### MIDI

`bassprog` 和 `chordprog` 接受额外的八度参数：

```
%%MIDI bassprog 22 octave=-1
%%MIDI chordprog 2 octave=1
```

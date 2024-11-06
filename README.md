## 关于字体
基本信息：

|信息     |  值   |
| --- | --- |
| 字体标准    |   2312汉字标准  |
|支持字数|6763
|字体类型|拼音汉字
|开源|是
|衬线|否
|holle world|a

这个字体的字号有点小，在用的时候注意调整大小
字体的制作人员名单（昵称）:

|名字     |
| --- |
|Vladimir15963     |
|otto |

特别感谢：

|名字     |
| --- | 
|银   | 
|迷雾|

字形的生成器是闭源的，你可去这里[字形生成器](https://github.com/SpeedyOrc-C/Honkai-3rd-II-Martian)用一个开源的字形生成器

## 什么是火星文?
「火星文」指的是在游戏《崩坏三》中出现的一种科幻文字，这种科幻文字本质上是中文字的变体，字形则是按拼音来写成的，关于火星文，有更详细的视频解析[视频链接](https://b23.tv/f8WnEch)
「火星文字形生成器」则是一个字形生成工具，用来生成每个汉字对应的火星字，按照拼音来自动生成图像，这还得感谢崩坏三设计的巧妙，我们不需要将每个字单独绘画。
## 如何开源?
字体本身是依照MIT开源协议进行开源，但是字形生成器并不开放，本篇笔记用来将字形生成器的计算逻辑，基本算法，字体生成器的基础构建，既使我没有将字形生成器开放，但可以通过这些笔记来做一个，不开放的原因有很多，比如写得太烂了，可读性一般，就写这篇笔记代替直接开放源码.
## 文星文的生成基础
根据崩坏三游戏里的逻辑生成对应字形(游戏官方末直接公开完整的设计，这里的生成规则按照B站视频获知)
在火星文中，每个单独的字都由其对应汉字的拼音组成，所以火星文字是一种拼音文字，每个字形最少由2个“拼符”组成，最多是6个“拼符”，拼符对应了汉字拼音的拉丁字母，如果这个字的拼音是奇数，则会加上一个占位符使其变为偶数。每个“拼符”可单独多乡5×5大小的网格，如果假设每个网格的像素为100×100,，则拼符大小是500×500。除了这些,将拼符组成为一个字，拼符与拼符之间相互重叠一个网格的大小，相邻方向重叠20%面积(重叠占比)。那用什么表示汉字拼音的四个声呢?用旋转表示，顺时针转0°,90°,180°270°,分别对应四个声调“āáǎà”，拼符旋转，字形(整体)不旋转，即在拼符组成字形之前旋转，占位符不参与旋转，例：如果一个字由3个拼符组成，带一个占位符，音调为三声，则这个字的三个拼符各自旋转180°,再组成这个字形.

## 制作过程
1. 拼符
在b站上有这期视频[视频链接](https://b23.tv/f8WnEch)，up主帮我们把所有拼符的图案找了出来，并且获得火星字形的生成方式
2. 字形生成
知道生成方式之后，我用 godot快速地做了一个字形生成器。这里有一个用JS实现的生成器，但是它不满足我的需求，所以虽然开源，但我不会js
我自制的字形生成器在二十分钟内把6763个汉字处理成对应的火星文字形图像
3. 字体制作
字体设计软件是FontCreator，这玩意不能批量导入，为了能自动地导入6763个图像，我们使用了按键精灵的脚本重复的执行导入图像，最后用自动的工具处理了字的边距和字宽

## 广告位
> 欢迎大家来ARG论坛来玩哇！链接：[迷雾论坛](https://www.mistarg.cn) 
> 还有QQ群链接：[QQ群](https://qm.qq.com/q/Prh0S9r128)


# 基础

## 字体属性

font-size

font-weight

font-style

font-family

font：style weight size/line-height family

## 文本属性

text-indent

line-height

text-decoration

text-align

## 背景属性

background-color

background-image

background-repeat

background-position

background：color image repeat position

## 盒子模型属性

box-sizing属性可以有两个值

content-box:默认值，设置的宽高只是内容宽高，边框和内边距会撑大盒子。

<img src="image/W3C标准盒模型content-box.jpg" style="zoom:67%;" />

border-box:设置的宽高是内容边框和内边距，设置边框和内边距会挤压内容的大小。

<img src="image/IE盒模型border-box.jpg" style="zoom: 67%;" />

**边框**

border-width

border-style   实线solid-虚线dashed-点线dotted

border-color

border连写   border：1px solid red；

给某个方向设置边框：border-方位名词

border-top:3px solid blue;

border-radius:参数可以为数值或者百分比的形式。

应用：若要正方形设置成一个圆，把border-radius设置为高度或宽度的一半或50%即可。

​			若是矩形设置成圆角矩形，把border-radius设置为高度的一半即可

**内边距**

padding-方位名词

padding连写：1-4个值都可以，从top顺时针赋值，没有的值取对面的。

**外边距**

margin-方位名词

margin连写：1-4个值都可以，从top顺时针赋值，没有的值取对面的。

**盒子阴影**

box-shadow:h-shadow v-shadow blur spread color inset

| 值       | 描述                                     |
| -------- | ---------------------------------------- |
| h-shadow | 必选。水平阴影的位置（x轴）。允许负值。  |
| v-shadow | 必选。垂直阴影的位置（y轴）。允许负值。  |
| blur     | 可选。模糊距离。                         |
| spread   | 可选，阴影的尺寸。                       |
| color    | 可选，阴影的颜色。可以是rgba。           |
| inset    | 可选，将外部阴影（outset）改为内部阴影。 |

**文字阴影**

text-shadow:h-shadow v-shadow blur  color

| 值       | 描述                                    |
| -------- | --------------------------------------- |
| h-shadow | 必选。水平阴影的位置（x轴）。允许负值。 |
| v-shadow | 必选。垂直阴影的位置（y轴）。允许负值。 |
| blur     | 可选。模糊距离。                        |
| color    | 可选，阴影的颜色。可以是rgba。          |

同盒子阴影。

## 浮动（float）

float属性用于创建浮动框，将其移动到一边，直到左边缘或右边缘触及包含块或另一个浮动框的边缘。

#### **浮动特性**

1.脱离标准流的控制（浮）  移动到指定位置（动），俗称脱标。浮动的盒子不再保留原先的位置。

2.如果多个盒子都设置了浮动，则它们会按照属性值一行内显示并且顶端对齐其排列。浮动的元素是互相贴靠在一起的（不会有缝隙），如果父级宽度装不下这些浮动的盒子，多出的盒子会另起一行对齐。

3.浮动的元素会具有行内块元素的特性，不管原先是什么模式的元素，添加浮动后都具有行内块元素相似的特性。 如果块级盒子没有设置宽度，默认宽度和父级一样宽，但是添加浮动后它的大小根据内容来决定。

#### **浮动的两个注意点**

1.浮动和标准流的父盒子搭配

先用标准流的父元素排列上下位置，之后内部子元素采取浮动排列左右位置。

2.一个盒子里面有多个盒子，如果其中一个盒子浮动了，那么其他的兄弟也应该浮动，以防止出现问题。浮动的盒子只会影响浮动盒子后面的标准流，不会影响前面的标准流。

#### **清除浮动**

为什么要清除浮动：由于父盒子多数情况下高度需要灵活设定（子盒子撑开父盒子的高度），但是当子盒子浮动后子盒子便不占有位置，会导致父盒子高度为零，进而影响下面的标准流。

清除浮动的本质：清除浮动的本质是清除浮动带来的影响，如果父元素设定了高度则不需要清除浮动，清楚浮动后父级就会根据子盒子的高度来自动设定高度。

清除浮动的方法：

**1.额外标签法（w3c推荐）**

在最后一个浮动的子元素后面添加一个额外标签，添加清除浮动样式。

如<div clear = 'both'></div>但是添加的标签不能是行内元素。

**2.父级添加overflow**

可以给父级添加overflow属性，将其属性值设置为hidden、auto或scroll。

最常见的是给父级添加overflow：hidden；

缺点：无法显示溢出的部分

**3.父级添加一个类名：after**

`.clearfix:after{`

`content:"",`

`display:block;`

`height:0;`

`clear:both;`

`visibility:hidden`

`}`

使用时复制这几行代码，给需要清除浮动的父元素加上clearfix类即可。

**4.双伪元素法**

与上一个方法类似

`.clearfix:before,.clearfix:after{`

`content:"",`

`display:table;`

`}`

`.clearfix:after{`

`clear:both;`

`}`

## 定位

position：

| 定位模式 | 是否脱标         | 移动位置                               |
| -------- | ---------------- | -------------------------------------- |
| static   | 否（占有位置）   | 不移动                                 |
| relative | 否（占有位置）   | 相对于自身原来的位置                   |
| absolute | 是（不占有位置） | 相对于有定位的祖先元素（没有则为body） |
| fixed    | 是（不占有位置） | 相对于浏览器可视区域                   |
| sticky   | 否（占有位置）   | 相对于浏览器可视区域                   |

#### 相对定位

position:relative 不脱标，相对定位是相对于自己原来的位置移动的。原来在标准流的位置继续占有，后面的盒子仍然以标准流的方式对待它。

#### 绝对定位

position:absolute  脱标，不再占有原来的位置，基于最近一级有定位的祖先元素为基准定位，如果没有祖先元素或者祖先元素全都没有定位则以body为基准定位。

应用：让一个绝对定位的盒子水平垂直居中

left:50%;

top:50%;

margin-left：负自己宽度的一半;

margin-top：负自己高度的一半;

#### 固定定位

position:fixed  脱标，不再占有原来的位置，以浏览器的可视窗口为参照移动元素，跟父元素没有任何关系，可以在浏览器页面滚动的时候元素的位置不发生改变。

应用：让一个固定定位的盒子始终紧贴版心的右侧

第一步：先让固定定位的盒子left：50%，走到浏览器可视区域一半的位置。

第二步：让固定定位的盒子margin-left：版心宽度一半的距离；

#### 粘性定位

position:sticky

1.以浏览器的可视窗口为参照点移动元素（固定定位的特点）

2.粘性定位占有原先的位置（相对定位的特点）

3.必须添加top、right、bottom、left中的其中一个才有效。

常用于导航栏。

#### z-index堆叠顺序

在使用定位布局的时候可能会产生盒子重叠的情况，此时可以使用z-index来决定谁在上谁在下。（z-index属性只对有定位的盒子生效）

z-index:1;     值可以是正整数、负整数和0，不可加单位。默认为auto，值大的在页面的上方。

如果属性值相同则按照书写顺序后来居上。

## 定位和浮动的类似与区别

绝对定位和固定定位在以下两点与浮动类似：

1.行内元素添加了绝对定位和固定定位后，可以直接设置宽度和高度。

2.块级元素添加了绝对定位和固定定位后，如果不设置宽度和高度，则默认宽度不再是100%，而是变为由内容的大小决定的。

3.浮动、绝对定位、固定定位的元素都不会出现外边距合并的问题。

浮动和定位对文字处理的不同：

当一个盒子浮动后，会”压住“后面标准流的盒子，但是如果标准流盒子里有文字，则文字会自动左移露出来。因为浮动最开始产生的原因就是做文字环绕效果。

而固定定位和绝对定位则会直接连同文字和后面标准流的盒子一起”压住“。

## 元素的显示与隐藏

**display**

display属性用于设置一个元素应如何显示，重点的属性值有两个。

1.display：none；

隐藏该元素，且不再占有原来的位置。

2.display:block;

除了转换为块级元素之外，同时还有显示元素的意思。

**visibility**

visibility属性用于指定一个元素可见还是隐藏，其默认值是inherited（继承父级），重点的属性有两个。

visibility：visible；

元素可视。

visibility：hidden；

元素隐藏，但是占有原来的位置。

**overflow**

overflow属性用于设置一个盒子其内容溢出盒子大小的时候会发生什么.

重点的属性值有 visible  hidden  scroll  auto

1.overflow:visible

直接在盒子外面显示

2.overflow:hidden

隐藏掉溢出的部分

3.overflow:scroll

添加滚动条（不过内容有没有溢出）

4.overflow:auto

在内容有溢出的时候自动添加滚动条

注意：如果是有定位的盒子，有时会设计某些元素在父盒子的外部显示（如挂件），此时要慎重使用overflow:hidden,它会隐藏掉溢出的部分。

## 其他

鼠标样式

表单或文本框取消轮廓线

文本域防止拖曳

垂直对齐vertical-align、底线基线中线顶线

单行文本溢出显示省略号

多行文本溢出显示省略号

# 进阶&应用（面试常问）

## css三大特性

**继承性：**

子元素有默认继承父元素某些样式的特点
	字体样式：color、font-style、font-weight、font-size、font-family
	文本样式：text-indent、text-align、line-height
	应用：可以直接给ul/ol设置list-style:none;，从而去除li默认样式。
	          可以直接给body设置统一的font-size，从而统一不同浏览器默认文字大小

**层叠性**：

​    给同一标签设置不同样式--样式叠加，都起作用
​	给同一标签设置相同样式--选择器优先级不同时根据优先级决定哪个样式生效
​			     --选择器优先级相同的时候写在最后的样式会生效

**优先级：**

继承 

< 通配符选择器 
< 标签选择器 （0，0，0，1）
< 类选择器 （0，0，1，0）
< id选择器 （0，1，0，0）
< 行内样式 （1，0，0，0）
< !important
	注意：!important不能提升继承的优先级
	           多个选择器权重可以相加，但是不存在进位

## css三种引入方式

内嵌 ：写在style标签中，style标签通常写在head标签中
外联 ：写在单独的css文件中，通过link标签在网页中引入，也可以通过@import引入
行内 ：写在标签的style属性中

## link和@import引入css

**html中引入外部的css文件有两种方式**

link引入形式：

```html
<link href="styles.css" type="text/css" />
```

@import引入形式：

```html
<style type="text/css">@import url("styles.css");</style>
```

**link和@import的区别**

1.适用范围不同

@import不仅可以在网页页面中使用，也可以在css文件中使用，这样可以将多个css文件引入到一个css文件中去。而link只能用于在网页中引入css文件。

2.功能有差异

link属于XHTML标签，而@import是css提供的一种方式。@import除了可以引入css，还可以定义rss、定义rel连接属性等。而@import只能加载css。

3.在页面中的加载顺序不同

当一个页面被加载时，link引入的css会被同时加载。而@import引用的css会在页面加载完毕后再加载，所以有时候浏览页面的时候最开始会没有样式，网速慢的时候比较明显。

4.兼容性

@import只在ie5以上才能支持，而link没有兼容性问题。不过我觉得在现在这个兼容性问题基本上可以忽略了。

5.权重不同

link引入的样式权重大于@import引入的样式。

6.使用DOM控制样式时的差别

如果想要使用js来控制dom去改变样式，只能通过link标签，@import不受dom的控制。

## 伪类和伪元素

## --BFC

BFC直译为"**块级格式化上下文**"。它是一个**独立的渲染区域**。简单来说就是，`BFC`是一个完全独立的空间（布局环境），让空间里的子元素不会影响到外面的布局。

**怎样触发BFC**

这里简单列举几个触发`BFC`使用的`CSS`属性

- overflow: hidden

- display: inline-block

- position: absolute

- position: fixed

- display: table-cell

- display: flex


**BFC的规则**

- `BFC`就是一个块级元素，块级元素会在垂直方向一个接一个的排列
- `BFC`就是页面中的一个隔离的独立容器，容器里的标签不会影响到外部标签
- 垂直方向的距离由margin决定， 属于同一个`BFC`的两个相邻的标签外边距会发生重叠
- 计算`BFC`的高度时，浮动元素也参与计算

**BFC解决了什么问题**

1.使用Float脱离文档流，高度塌陷

2.Margin边距重叠

## 外边距塌陷问题

主要有两种情况：

第一种是上下两个兄弟盒子之间，如果上面的盒子有下边距值，下面的盒子有上边距值，这时两个盒子实际上显示出来的外边距是两者之中较大的那一个。

解决方法：只给其中一个盒子添加外边距。

第二种是父子两个盒子嵌套，父子盒子都有上边距，此时子盒子的上边距不会生效，而是紧贴着父元素的上边界，而父元素的上边距会取父元素和子元素上边距较大的那个值。

解决方法： 给父盒子加上边框

​					 给父盒子加上内边距

​					为父元素添加overflow：hidden（常用）

## 垂直水平居中的几种方式

**1.利用flex布局实现**

把父元素设置为 flex 或者 inline-flex，使其中的盒子沿主轴和交叉轴水平垂直居中。

```css
父盒子{
    display: flex;
	justify-content: center;
	align-items: center;
}
```

**2.使用 position + margin 负边距实现**

如果已知子盒子宽高的话。可以给父元素设置相对定位，给子元素设置绝对定位
再让子元素沿上方和左方偏移 50% 的父元素高宽，但因为是根据左上角偏移的
所以要用负边距 margin 来修正，修正的大小为宽高的一半。

```css
父盒子{
	position: relative;
}
子盒子{
	position: absolute;
	left: 50%;
	top: 50%;
	margin: -子盒子高度一半px 0 0 -子盒子宽度一半px;
    /*即设置margin-top和margin-left*/
}
```

**3.使用 position + transform 实现**

如果不知道子盒子的宽度和高度，可以使用position + transform实现，已知子盒子宽高也可以使用这种方法。

```
父盒子{
	position: relative;
}
子盒子{
	position: absolute;
	left: 50%;
	top: 50%;
	transform: translate(-50%, -50%);
}
```

## meta viewport 原理

 viewprot是用户网页的可视区域。

 meta viewport 标签的作用是让当前 viewport 的宽度等于设备的宽度，同时不允许用户进行手动缩放

 viewport的原理：手机浏览器是把页面房子啊一个虚拟的“窗口（viewport）”比屏幕宽，这样就不用把每个网页挤到很小的窗口中（这样会破坏没有针对手机浏览器优化的网页的布局），用户可以通过平移和缩放来看网页的不同部分；

 目的是正常展示没有做移动端适配的网页，让他们完整的展示给用户；

viewport和移动端布局

viewport（视口），就是浏览器显示页面内容的屏幕区域
layout viewport（布局视口），分辨率一般设置为980px，用于解决早期页面在手机上显示的问题
visual viewport（视觉视口），物理屏幕的可视区域，屏幕显示器的物理像素
ideal viewport（理想视口），屏幕分辨率

## 利用css实现三角

# CSS3

## flex布局

+ flex 是 flexible Box 的缩写，意为"弹性布局"，用来为盒状模型提供最大的灵活性，任何一个容器都可以指定为 flex 布局。
+ 当我们为父盒子设为 flex 布局以后，子元素的 float、clear 和 vertical-align 属性将失效。
+ flex布局又叫伸缩布局 、弹性布局 、伸缩盒布局 、弹性盒布局 
+ 采用 Flex 布局的元素，称为 Flex 容器（flexcontainer），简称"容器"。它的所有子元素自动成为容器成员，称为 Flex 项目（flexitem），简称"项目"。

**总结**：就是通过给父盒子添加flex属性，来控制子盒子的位置和排列方式

### flex布局常见的父元素属性：

#### flex-direction设置主轴的方向

row：从左到右（默认值）

row-reverse：从右向左

column：从上到下

column-reverse：从下到上

#### justify-content设置主轴上的子元素排列方式

flex-start：贴着主轴头部

flex-end：贴着主轴尾部

center：在主轴居中对齐

space-around：平分剩余空间

space-between：先两边贴边，再平分剩余空间

#### flex-wrap设置是否换行

默认情况下，项目都排在一条线上，不会换行。

nowrap：不换行（默认）

wrap：换行

#### align-items 设置侧轴上的子元素排列方式（单行 ）

该属性是控制子项在侧轴上的排列方式  在子项为单行的时候使用。

flex-start：贴着侧轴头部

flex-end：贴着侧轴尾部

center：在侧轴居中

stretch：拉伸（子项元素高度平分父元素高度）

#### align-content设置侧轴上的子元素的排列方式（多行）

flex-start：贴着侧轴头部

flex-end：贴着侧轴尾部

center：在侧轴居中

stretch：拉伸（子项元素高度平分父元素高度）

space-around：子项在侧轴平分剩余空间

space-between：子项在侧轴先分布在两侧，再平分剩余空间

#### flex-flow属性是flex-direction和flex-wrap属性的复合属性

如flex-flow:row wrap;

### flex布局常见的子元素属性：

#### flex子元素占的份数

flex属性定义子元素分配剩余空间，用flex的值表示占多少份

默认为0

#### align-self控制子元素自己在侧轴上的排列方式

align-self 属性允许单个项目有与其他项目不一样的对齐方式，可覆盖 align-items 属性。

默认值为 auto，表示继承父元素的 align-items 属性，如果没有父元素，则等同于 stretch。

flex-start：贴着侧轴头部

flex-end：贴着侧轴尾部

center：在侧轴居中

stretch：拉伸（子项元素高度平分父元素高度）

#### order属性定义项目的排列顺序

数值越小，排列越靠前，默认为0。
# 认识CSS

Css用于添加颜色，样式，就像给他画画一样

## 两种语法

```css
/* 注释 */
选择器 {
    属性:值;
    属性:值;
}

@关键字 {
	其他
}
```

## 三种引入的方式

1. `<link rel="stylesheet" href="index.css">` 在head标签下引入

   `rel`必须写入`stylesheet`,`href`是文件的本地地址

2. `@import "文件地址"` 需要在style标签下引入

   ```css
   <style>
   	@import "index.css";
   </style>
   ```

   需要注意 必须写在`style`标签下, 

   必须写在style的前面，

   `@import "index.css"` 地址后面必须加上 **`;`**号

   可以嵌套在link引入文件中

3. 内部引入

   在HTML结构里面添加一个`style`里面写样式

   ```css
   <!DOCTYPE html>
   <html lang="en">
   <head>
       <meta charset="UTF-8">
       <meta name="viewport" content="width=device-width, initial-scale=1.0">
       <title>Document</title>
       <!-- 第一种引入方法 -->
       <link rel="stylesheet" href="index.css">
   	<!-- 第二种引入方法 -->
       <style>
           /* 第三种引用 
               可以嵌套在 link引用的css里
           */
           @import "index.css";
           
       </style>
   </head>
   <body>
       
   </body>
   </html>
   ```

   

### `link`方式和`@import`引入CSS有什么区别

1. `<link>`是HTML的标签，在页面上代表着一个元素，可以被JS修改，`@import`是CSS语法，所以JS无法操作
2. 两个`<link>`标签，文件并行加载.一个`<link`的CSS里包含一个`@import`，文件串行加载会更慢，因此不推荐使用`@improt`CSS属性进行引入;



# CSS选择器类型

有CSS选择，伪元素和伪类

## 学习目标

- 掌握记住选择器写法

- 掌握常见伪类伪元素的用法

## 通配选择器

> 选中全部或者选择其中的全部

```
 * {  color: red }
 *.app{ color:red}
```

## 类选择器 与 ID 选择器

> 类选择器是通过 class来选择对应的标签 ，ID选择器是通过标签中的ID进行一个选择

```
 #id { color: red;}
 .class { color: red}
```

## 元素选择器

> 比如标签叫 span就等于页面的元素，通过标签来选择

## 普通兄弟选择器

> A ~ B 在父级相同的AB下，选择A元素同层级的B元素

## 相邻兄弟选择器

> A + B 在父级相同的情况下，选择A元素同层级的B元素第一个;

## 后代选择器

> A B 在父级的后代都被选中；比如A父级后代的B，满足全部选中

## 属性选择器

> [attr] 代表命名的属性元素

1. [attr = val] ---- 表示attr命名的属性，属性值为val的元素被选中
2. [attr~=val] --- 表示attr命名的属性，属性为vall为空格分隔的列表被选中
3. [attr^=val] --- 表示attr命名的属性，属性值为val为开头的被选中
4. [attr$=val] --- 表示attr命名的属性，属性值为val为结尾的被选中
5. [attr*=val] --- 表示attr命名的属性，属性值至少包含一个val的被选中

## 链接标签伪类

```
 /* 选中未访问的链接 */
  a:link {}
  
 /*  选中访问过的链接*/
  a:visited { }

 /*  选中鼠标放置上的链接*/
  a:hover { }
```

## 表单的伪类

```
 /*  被勾选的表单元素*/
 input:checked {}

 /* 选中被激活的表单元素 */
 input:focus { }
```

## 选择对应的标签伪类

> [.box]为一个元素

```
   /*  选择 box 第一个孩子*/
.box :first-child { } 

 /* 选择box 第x个孩子  */
.box :nth-child(x) { }

 /*  选择box 最后一个孩子*/
.box :last-child { }

 /* 选择box标签元素一样，第一个孩子 */
.box :first-of-type { }
 /*  选择box标签元素一样，第x个孩子*/
.box :nth-of-type(x) { }
 /*  选择box标签元素一样，第后一个孩子*/
.box :last-of-type { }
```

## URL与 ID 触发的伪类

> :target CSS 伪类 代表一个唯一的页面元素(目标元素)，其id 与当前URL片段匹配 .

## 匹配不符合一组选择器的元素

> :not() 用来匹配不符合一组选择器的元素。由于它的作用是防止特定的元素被选中，它也被称为反选伪类



## 更多::伪类

1. ::before 在标签开头添加一段内容

> 需要配合 CSS:content属性来写

```CSS
.box::before{
    content: "字体"
}
```

2. ::after 在标签结尾添加一段内容 

> 配合 CSS：`content`属性

```css
.box::after{
    content:'字体'
}
```

3. ::first-line 、::first-letter 、 ::selection

> 分别是：选中段落第一行,选中段落第一个字符、鼠标选中的段落

```css
.box::first-line{
    /*属性*/
}
.box::first-letter {
    /* 属性*/
}
::selection {
    /*属性*/
}
```



# CSS概念

基本了解层叠，优先级、继承如何工作的

## 层叠	

CSS顺序很重要，当两个同级的选择器中的元素属性一样的时候，会执行最后一个选择器的元素属性

## 优先级

ID选择器与类选择器都是同一个元素标签，ID选择器权重级会比类选择器高，就会执行ID选择器；

`!important(迫不得已再写) > 内联样式 > 选择器设置样式 > 浏览器默认样式 > 继承样式`

**不同属性会叠加、相同属性会覆盖**

- 选择器优先级不同:优先级高的会覆盖优先级低的
- 选择器优先级相同:后面的会覆盖前面的



## 继承

父级中设置的CSS会继承到子级中，比如父级设置的color颜色会继承到子级的标签中，有些属性不能被继承，比如：宽度、边框、等;

继承属性：color、font-size、font-family、line-height.. 大多数是文字之类的

非继承属性: border 、background、边框、内边距、等、改变形状的;

控制继承

- `inherit` 使用继承自父级的样式
- `initial` 使用该属性的默认值 initial value
- `unset` 如果是继承属性会继承父级，如果是非继承就会用initlial value默认值.



# 盒模型

> 分别 块盒型 、内联盒型

块盒型（`block`）

- 填满一行的宽度，会换行、宽度高度都可以修改，内边距、外边距、边框都可以影响当前盒子周围推开
- 比如`div,p、ul、ol、healer`等等

内联盒型

- 不会换行、高度宽度不能修改，内边距、外边距、边框（左右会影响周围的字体推开）上下效果会生效则不会影响周围;
- 比如` span、a 、 i 、 em 、 strong 、 img 、 input 、 label 、 selcet ` 

## 盒模型属性

> display 取决于用什么模型

**display**属性：

- block - 块盒型
- inline - 内联盒型
- inline-block 块内合型
- flex - flex弹性布局
- grid - grid网格布局

**margin**属性外边距：上、右、下、左

**padding**属性内边距: 上、右、下、左

**border**属性边框：上、右、下、左

**width**宽、**height**高;

## 盒模型形成

> 怎么组成的盒模型，都有哪些元素，怎么计算的

### 盒模型的形成

- **Content box**: 这个区域是用来**显示内容**，大小可以通过设置 [`width`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/width) 和 [`height`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/height).
- **Padding box**: 包围在**内容区域外部的空白区域**； 大小通过 [`padding`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/padding) 相关属性设置。
- **Border box**: 边框盒**包裹内容和内边距**。大小通过 [`border`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border) 相关属性设置。
- **Margin box**: 这是最外面的区域，是**盒子和其他元素之间的空白区域**。大小通过 [`margin`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/margin) 相关属性设置。

![标装盒模型](https://mdn.mozillademos.org/files/16558/box-model.png)

### 标准盒模型 

整个人盒子计算方式 = 宽 width + padding(左右) + margin(左右) + border(左右)

 								= 高 height + padding(上下) + margin(上下) + border(上下)

### IE盒模型

有个特别之处,你固定的宽高，你添加了外边距内边距会把你宽高减少计算进去

只需要添加： `box-sizing:border-box`



## 文本样式属性

- **color**文本颜色
- **font-size**文本大小 
- **vw - vh** 宽高适配移动端
- **font-family**适配图标、文本的字体格式
- **font-stlye**文字斜体设置
- **font-weight**设置文字粗细

关于设置样式的
- text-decotation 设置文字划线（下化，中化等）;
- text-transform 转化 大小写字母和首字母大小写 
- text-align 居中 左 右 都可以 局限于 块盒型

关于溢出和是否处理换行
- white-space 是否处理换行（nowrap推荐）
- overflow 处理内容太大场景，应用到块盒型
- text-overflow 溢出处理 

HTML标签

```HTml
ol+li 有序列表
ul+li 无序列表
dl+dt+dd 自定义列表

per code 用来自定义写东西 比如 空格 1 空格 就显示 空格 1 空格
hr 下划线
br 换行 
em 强调关键词会"加粗斜"
strong 重要逻辑上的强调
b 物理上变粗，不用强调
blockquote 引入的引语

```

H5语言化标签

`<section>`章节

`<article>`文章

`<header>`头部

`<footer>`尾部

`<main>`主要内容

`<aside>`次要内容

`<nav>`导航条

全局属性

> 所有标签都共有的属性

```html
标记标签属性
class标签（用来精准标注到哪个标签） 
<div class="step"></div>
id标签（每个人都有一个ID或者说一大块区域就可以使用ID）
<div id="hello"></div>
style属性（用于在标签里写CSS）
<div stlye='color:bule'>hello</div>
title属性（鼠标放到内容标签内可以出现提示）
<div title='hello'>hello</div>
contenteditable属性(可以进行编辑)
<div contenteditable>hello</div>
tabindex用于表单填写tap切换（从高往低切）
<input text='text' tabindex=1>
<input text='text' tabindex=2>
<input text='text' tabindex=3>
hidden属性用于隐藏标签
<div hidden>hello</div>

```

笔试面试题

```text
	id与class有什么区别
id表示独一无二的，一个元素只能有一个id，不同的元素不能有相同的id
class表示 特征，像这个标签与标签同样的可以一起并用，不同的标签可以使用相同的class，一个标签可以存在多个class

	Web页面分为哪三层，分别是什么？
结构层（HTML）
表现层（css）
行为层(JS)

	HTML语义化
便于开发阅读，便于搜索引x理解，便于读屏器阅读

```



## 重要的跳转链接

1.让其他网页嵌套到网页中

> 使用  `iframe`来完成

```html
 <iframe src="https://www.baidu.com/" frameborder="0"></iframe> //显示百度
```

2.超链接

> `a`标签超链接：`href`,`title`,`target`

- `href`用于跳转链接，路径，伪协议，锚点

> 链接`//baidu.com`,路径：`本地路径`,伪协议:`javascript:代码，mailto：邮箱，tcl：电话`
> 锚点:`#ID地址`

- `title`全局属性，鼠标触碰显示标签
- `target`用于在指定网页刷新，还是新开窗口刷新

> target:"`_blank`新窗口刷新，`_self`本页面刷新，
> `_prent`父级框架加载，`_top`最顶级框架加载"

- `dowmload`用于下载链接

  ```html
  <a href="https://www.baidu.com" dowmload>下载百度页面</a>
  <!--dowmload可以设置参数-->
  <a href="https://www.baidu.com" dowmload='我是百度页面'>下载百度页面</a>
  <!--我是百度页面是下载名字-->
  ```

## 表格标签

> 表格标签是为了方便写一些需求的结构表格

  ```html
<table>
    <!--语义化：表格头部-->
    <thead>
        <!--表格行列-->
        <tr>
            <!--表格头部-->
            <th></th>
        </tr>
    </thead>
    <!--语义化：表格身体-->
    <tbody>
        <tr>
            <!--表格单元-->
            <td></td>
        </tr>
    </tbody>
    <!--语义化:表格尾部-->
    <tfoot>
        <td colspan='2'></td>
    </tfoot>
</table>
  ```

标签元素属性

- `colspan='合并单元'`行合并几个单元格
- `rowsapn='横列合并'`横列合并几个单元格

特殊表格标签

- `caption`表头描述
- `colgroup`让第几个单元格改变样式

```html
  <table>
        <caption>我是学生表格</caption>
        <colgroup>
            <col>
            <col span="2" class="batman">
            <col span="2" class="falsh">
        </colgroup>
        <tr>
            <td > </td>
            <th scope="col">Batman</th>
            <th scope="col">Robin</th>
            <th scope="col">The Flash</th>
            <th scope="col">Kid Flash</th>
        </tr>
        <tr>
            <th scope="row">Skill</th>
            <td>Smarts</td>
            <td>Dex, acrobat</td>
            <td>Super speed</td>
            <td>Super speed</td>
        </tr>

    </table>
```

col的`span`是让`th`的前两个表格定义`calss=“batman”`样式，最后两个同上

th里的scope是为了col的定义，让col的样式同步

th的row是为了让上面的格子一样颜色；



## 表单提交 from

提交数据，收集数据到服务器，有两个标签属性:

1.action发送到某个接口或者网站,请求的接口

```html
<from action="/login"></from>
```

2.method表单请求：是用GET 还是 POST

```html
<from action='/login' method="GET"></from>
```



### 表单填写 input

> 功能比较多，按需求来写

标签属性:

1.提示类

- *placeholder* 在表单里引导用户这里需要填写什么内容
- *required* 在表单留空提交，会提示你需要填写这个表单
- *value*默认为空，如给值，表单会显示你写的value
- name标签属性告诉后端这个标签收集什么类型或者什么东西

2.功能类

- *autofocus*自动焦点表单，提高用户体验
- *tabindex*切换焦点 以（1）低到高（10） 0为最后，-1为不选择
- *disabled* 不能被选择到表单
- checked 默认选择(类型 checkbox生效)

input表单type类型

1. 勾选

   `radio`单选类型(如果需要分组请name填写为一样)

   `checkbox`多选类型(如想默认选择  checked 默认选择）

2. 加密

   `hidden`隐藏加密，可以请求发送之类的 防止CSRF攻击

3. 格式类型

   `password`密码格式

   `text`填写信息格式

   `email`只能以邮箱格式

   `number`只能数字格式

   `tel`只能电话类型

   `url`只能网站类型

4. 按钮提交与组件

   `submit`提交默认按钮

   `button`按钮提交配合ajax请求

   `reset`重置按钮，比如表单输入信息重新填写
   `file`提交文件
   `dete` 日期组件
   `time` 时间组件
   `range`进度条组件

### label-for 触发对应的焦点

```html
<label for='xx'>
	<input tpye='text' id="xx" placeholder='用户名'> 
</label>
```

label-for 与 input-id的值要为一样，不然无法触发对应的表单的焦点

### select-option下拉选项

```html
<select name='sel'>
    <option value='aa' selected>aa</option>
    <option value='bb'>bb</option>
</select>
```

`select`的name代表的是 提交给后端的名字

`option`的value代表的是 对应的选择的对象 比如 option是aa，用户选择的是aa，返回给后端就是 sel = aa

所以 select的name 用于 提交给后端组别，option的value是组别的选择

### GET和POST提交的数据的区别

1.提交数据的形式不一样

​	GET提交一条拼接很长的URL形式来提交

​	POST提交是原来的URL来提交

2.提交的数据大小

​	GET提交数据大小，有限制，根据浏览器来判断

​	POST提交数据大小，没有限制

3.安全性

​	理论上两个都不安全，但是`post`的参数不在`url`，相对于`get`隐蔽性会好一点

4.缓冲性

​	`GET`是可缓冲的

​	`POST`是不可缓冲的
## 简介
**Cascading Style Sheets (CSS) 层叠样式表**

## 层叠及继承
**层叠主要的三种样式来源：**
* 浏览器对HTML定义的默认样式。
* 用户定义的样式。
* 开发者定义的样式，可以有三种形式：
  + 定义在外部文件（外链样式）
  + 在页面的头部定义（内联样式）
  + 定义在特定的元素身上（行内样式）：多用于测试，可维护性较差。
<br />

  ```js
  优先级:
  1. 用户定义 > 默认样式 > 开发者样式
  2. 子元素自身的样式 < 从父级继承的样式
  ```
  
## 选择器
**类选择器 (class selector)**
* 多个元素可共享一个类名.
* 以 (.) 开头.
<br />

**ID 选择器 (ID selector)**
* 必须唯一.
* 以 (#) 开头.

```js
当多个规则指定了相同的属性值应用到一个元素上时:
1. 拥有更高确定度的选择器优先级更高.
2. 当确定度相同, 后出现的规则优先级高.
3. ID selector < class selector < tag selector
```

**伪类选择器(pseudo-classes selectors)**
* CSS伪类（pseudo-class）是加在选择器后面的用来指定元素状态的关键字。
* 常见的基于关系的选择器

选择器 | 选择的元素
------------ | -------------
A E      | 元素A的任一后代元素E (后代节点指A的子节点，子节点的子节点，以此类推)
A > E      | 元素A的任一子元素E(也就是直系后代)
E:first-child      | 任一是其父母结点的第一个子节点的元素E)
B + E      | 元素B的任一下一个兄弟元素E 
B ~ E     | B元素后面的拥有共同父元素的兄弟元素E

**实例: 创建纯CSS无JavaScript的下拉菜单**
```js
div.menu-bar ul ul {
 display: none;
}
div.menu-bar li:hover > ul {
  display: block;
}
```

## 文本样式
**字体 (font)**
* 字体加粗 (font-weight)
* 字体的风格 (font-style)
* 装饰 (text-decoration: underline/line-througn/none)
* 小型大写字母 (font-variant: small-caps; 指定文本为小型大写字母.)
* 字体的大小 (font-size)
  + 使用系统内置的值: small, medium, large.
  + 相对父元素大小的值: smaller, larger, 150%/1.5em.
  + 指定实际大小: 14px(像素), 14pt(点)
  
* 行高 (line-height)
* 字体 (font family)

```js
p {font: italic 75%/125% "Comic Sans MS", cursive;}
```

> 1. 字体为斜体
> 2. 字体大小为父元素字体 3/4, 行高设置为 125%
> 3. 字体为 CSM, 当浏览器不支持, 使用默认字体: cursive. 
    * CSM, cursive 不支持斜体.
> 4. 省略 bold / small-caps 选项**


## 颜色
**属性**
* 元素的背景色: background-color
  1. transparent  属性将移除所有颜色, 呈现出父元素的背景色.


## 文本
**内容**
* 在元素的前后插入文本: 在选择器后面加上 :before, :after.
* 在声明中指定 content 属性.
  + 文本
  ```js
  .ref: before {
   font-weight: bold;
   color: navy;
   content: "reference: ";
   }
  ``` 
  + 图片 
  ```js
  a.glossary:after {content: " " url("../images/glossary-ico.gif");)
  ```
  > 插入一个空格和图标
  
  + 背景图片
  ```js
  #sidebar-box {background: url("../images/sidebar-ground.png") no repeated;)
  ```
  > 背景图默认是 repeat（重复）的，水平和垂直方向重复.
  
  
## 列表
* list-style 属性
* 无序列表: 
 * 三种标记样式: 
  + disc
  + circle
  + square
* 有序列表:
  + decimal
  + lower-roman
  + upper-roman
  + lower-latin
  + upper-latin
* 计数器
 + 计数开始前, 用 counter-reset 属性重置计数器
 + 设置 counter-increment: 计数器名
 + 在选择器增加 :before 或 a:after 
 + 设置 content: counter()
 
 '''js
 h3.numbered {counter-reset: mynum;} /* 初始化计数器 mynum */
 
 p.numbered:before {
  content: counter(mynum) ": "; /* 序列后加上 (: ) */
  counter-increment: mynum;
  font-weight: bold;
 }
  

## 盒模型
* 内边距总是跟元素的背景色一致 (padding)
* 外边距总是透明的 (margin)
* 边框: border 属性
  + solid
  + dotted
  + dashed
  + double
  + inset
  + outset
  + ridge
  + groove
    * none 或 hidden 移除边框
    * transparent 让边框不可见, 后者不会改变布局
    * 指定某一方向边框: border-top/right/bottom/left.
    
## 布局
* 文档结构: <div> 元素创建结构(容器).
* 大小单位: 建议使用 % / em, em 通常是当前字体大小. 当用户改变字体大小时, 布局会自我调整.
* 文本布局: 元素内容的对齐方式. 可应用于任何文本类内容, 不只是纯文本.
  + text-algin: 内容对齐, left, right, center, justify.
  + text-index: 指定内容缩进.
  >**默认情况下子元素将继承， 需要在子元素中将其关闭，以免出现意想不到的效果。**
  >**标题之后的内容并不属于标题。当你对齐一个标题时，其后的元素不会继承该样式。**
* 浮动: float 属性: 或.
  + 强制元素靠左或靠右: float: left/right.
  + 避免元素受到浮动影响: clear: left/right.
* 位置: 属性含 top, right, bottom, left, width, height (除 static 外)
  + relative:
    * 通过为元素指定一个值，元素相对于其原来位置移动。也可以使用margin来达到同样的效果。
  + fixed:
    * 为元素指定相对于窗口的确切位置 。即使文档的其它元素出现滚动，元素位置仍然不变。
  + absolute: 
    * 为元素指定相对于其父元素的确切位置。只有在父元素使用 relative, fixed or absolute 时才有效。
  + static
    * 默认值。当明确要关闭位置属性时使用。
 
## 表格
* 单元格无外边距, 有边框及内边距.
  + 边框被表格的 border-spacing 属性值间隔(默认), 用 border-collapse: collapse 移除.
* 标题: 
  + <caption> 元素是用在整个表格的一个标签。默认下，它显示在表格的顶部。
  + caption-side: bottom 属性将标签移到表格的底部。
* 空单元格
  + 显示空单元格 empty-cells: show 
  + 隐藏空单元格 empty-cells: hide (单元格的父元素设置了背景, 将呈现在空白区域内)
* 结构
```js
<table>
  <caption>
    <thead>
      <tr>
        <th>
    <tbody>
      <tr>
        <th>
        <td>
    <tfoot>
```

## 媒体
**常见媒介类型**

名称 | 内容
------------ | -------------
screen       | 彩色计算机显示
print       | 打印 (分页式媒体)
projection       | 投影
all       | 所有媒体(默认)

* 导航区域的父元素的 id 为: nav-area.
* HTML5 使用 <nav> 元素代替带有 id 属性的 <div>

**medio**
* @media 格式对特定的媒介指定适配规则.
  + 打印网页时, 添加一条适配规则, 可将导航区域隐藏.
    ```js
    @media print {
      #nav-area {display: none;}
      }
    ```
  + 通过 <link> 标签上添加 media 属性来指定媒介类型.
  + 在样式表开头使用 @import 一个 url 引入另外的样式表, 同时指定其媒介类型.

**用户界面**

Selector |	Selects
------------ | -------------
E:hover | 当鼠标悬浮任何E元素上
E:focus | 当元素获得键盘焦点
E:active |	当元素是当前的活动元素
E:link | 	当元素超链接到一个url但是用户还没有访问过
E:visited |	当元素超链接到一个url但是用户已经访问过


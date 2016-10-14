# HTML - HyperText Markup Language 超文本标记语言

## 简介
* HTML 是一个国际化的标准，由万维网联盟（W3C）和网页超文本技术工作小组 (WHATWG)维护。
* HTML 规范包括较为松散的HTML语法及更为严格的 XML（Extensible Markup Language 扩展标记语言）语法.

## 语法

### HTML 表单用于搜集不同类型的用户输入.
* <form> 元素: 定义 HTML 表单.
  + <input> 元素: 含有不同的 type 属性.
  
  类型 | 描述
  ---- | ----
  text | 定义常规文本输入
  radio | 定义单选按钮输入 
  checkbox | 定义复选框输入
  submit | 定义提交按钮 (提交表单)
  password | 定义密码字段 (字段中有掩码显示)
  
    * <input type = "text">: 文件输入
    ```js
    <input type = "text" name = "firstname">First name
    ```
    
    * <input type = "radio">: 单选按钮
    ```js>
    <input type = "radio" name = "sex" value = "male" checked>Male
    <input type = 'radio' name = "sex" value = "female">Female
    /* checked 选项为: 默认选择 */
    /* name 值必须一致 */
    /* value 为框内默认字体 */
    ```
    
    * <input type = "checkbox">: 复选框
    ```js
    <input type = "checkbox" name = "vehicle" value = "Bike">
    ```
    
    * <input type = "submit">: 提交按钮
    ```js
    <input type = "submit" value = "Submit">Submit
    /* 省略了提交按钮的 value 属性，将获得默认文本 */
    ```
    
  + Action 属性: 提交表单时执行的动作
  ```js
  <form action = "action_page.php">
  /* 1. 指定某个服务器脚本处理被提交表单 */
  /* 2. 省略属性, 默认为当前页面 */
  ```
  
  + Method 属性:　在提交表单时所用的 HTTP 方法（GET 或 POST)
  ```js
  <form action = "action_page.php" method = "GET">
  <form action = "action_page.php" method = "POST">
  ```

    * GET (默认方法): 适合少量数据的提交, 浏览器会设定容量限制.
    * POST: 安全性高, 页面地址栏被提交的数据是不可见的.
  + Name 属性: 每个输入字段必须设置一个 name 属性.
  + <fieldset> 元素: 结合表单中的相关数据. 
    * <legend> 元素: 为 <fieldset> 元素定义标题
  ```js
  <form actipn = "action_page.php">
  <fieldset>
  <legend>Personal information:</legend>
  </fieldset>
  </form>
  ```
  
* 完整版
```js
<form action = 'action_page.php' method = "GET" target = "_blank" accept-charset = "UTF-8" ectype = "applicatipn/x-www-form-urlencoded" autocomplete = "off" novalidate>
...
</form>
```

* 清单

属性 | 描述
---- | ----
accept-charset | 规定在被提交表单中使用的字符集（默认：页面字符集）。
action | 规定向何处提交表单的地址（URL）（提交页面）。
autocomplete | 规定浏览器应该自动完成表单（默认：开启）。
enctype  | 规定被提交数据的编码（默认：url-encoded）。
method | 规定在提交表单时所用的 HTTP 方法（默认：GET）。
name | 规定识别表单的名称（对于 DOM 使用：document.forms.name）。
novalidate | 规定浏览器不验证表单。
target | 规定 action 属性中地址的目标（默认：_self） 

<br />

### 表单元素
* \<select> 元素: (下拉列表).
* \<option> 元素: 待选择的选项.
  + 默认显示为: 首个选项.
  + 添加 selected 属性为预定义选项
  ```js
  <select name = "cars">
  <option value = "volvo">Volvo</option>
  <option value = "saab">Saab</option>
  <option value = "fiat">Fiat</option>
  <option value = "audi">Audi</option>
  </select>
  ```

* \<textarea> 元素: 定义多行输入字段(文本域):
```js
<textarea name = "message" rows = "10" cols = "30">
blablablalala
</textarea>
```

* \<button> 元素: 定义可点击的按钮
```js
<button type = "button" onclik = "alert('hello world!')">Click me!</button>"
```

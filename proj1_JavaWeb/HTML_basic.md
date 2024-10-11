# HTML

## Markup language
- 双标签： 开始标签和结束标签构成完整标签，中间内容是 文本标签体，即**标签体**
  - ```html <p>HTML is a very popular for-end technology.</p>```
- 单标签： 
  - ```html <input type="text" name="username" />```
- 属性：
  - ```html <a href="https://www.xxx.com"> show detail </a>```

## HTML structure

<div style="text-align:center">
    <img src="/proj1_JavaWeb/pic_src/HTML 结构.png" alt="HTML 结构.png" style="margin-bottom: 1px;">
    <p>HTML 结构</p>
</div>

- 注释 
```html 
<!---->
```
- 根标签 
```html 
<html>

</html>
```
- 头标签: 定义不直接展示在页面主体上但是又很重要的内容
  - 如 字符集、CSS引入、js引入、其他...
  - 文档声明：
  - 文档标题： title
  - 网页编码格式：charset
  - HTML文档元数据：meta (但标签)
```html 
<html>
    <head>
        <!DOCTYPE html>
        <title> this is a documental title</title>
        <meta charset="utf-8" />
    </head>
</html>
```
- 体标签: 定义到要展示到页面主题的内容
  - 标题： h1 到 h6 定义
  - 段落： p
  - 连接： a
  - 图像： img
```html 
<html>
    <head>
        <!DOCTYPE html>
        <title> this is a documental title</title>
        <meta charset="utf-8" />
    </head>
    <body>
        <h1> this is a headline </h1>
        <p> this is a paragraph </p>
        <a href="https://www.baidu.com"> this is a url </a>
        <img src="/proj1_JavaWeb/pic_src/HTML 结构.png" width="258" height="39" />
    </body>
</html>
```

## HTML Details
### specialized vocabulary
标签 tag             页面的一对 <>
属性 attribute       对标签特征进行设置的一种方式，一般在开始标签中定义
文本 text            双标签中间的文字
元素 element         "开始标签 + 属性 + 文本 + 结束标签"  为一个元素

### more syntax
1. root tag只有一个
2. 单双标签都要正确关闭
3. 标签可以嵌套，但是不能交叉嵌套
4. 注释不能嵌套
5. 属性必须有值，值必须加引号，H5中属性名和值相同时可以省略属性值
6. HTML中不严格区分字符串使用单双引号
7. HTML标签不严格区分大小写，但是不能大小写混用
8. HTML中不允许自定义标签名
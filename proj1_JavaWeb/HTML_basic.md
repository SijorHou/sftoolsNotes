# HTML
`shift + Alt + F` 一键格式化 vscode html代码
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
- 根标签 html 
```html 
<html>

</html>
```
- 头标签 head: 定义不直接展示在页面主体上但是又很重要的内容
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
- 体标签 body: 定义到要展示到页面主题的内容
  - 标题： h1 到 h6 定义
  - 段落： p
  - 链接： a
  - 图像： img
  - 水平线：hr
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
        <hr>
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


### common tag, paragraph, line-break
- `<br>` 换行
- `<hr>` 插入水平线
- `<a ..>link_tar_dercription</a>` 链接标签
    - `href (url, relative_path, asolute_path)`
    - `target (_self, _blank)`
    - `<a href="www.baidu.com"/"local_target_src.html" target="_self/_blank">target description</a>`
- `<img ../>` 图像标签
  - `src, title, alt, height, width`
  - `<img src="pic_src_addr" title="hover notes" alt="failed loading notes" height="300px/50%" width="300/30%"/>`
  - 更精细的格式控制可以通过 CSS 实现
- `<ol></ol>, <ul></ul>` 列表（order-list有序列表， 无序列表）
  - `<li>list_item_name</li>` 列表项定义内容
- `<table> ..tx.. </table>` 表格
  - `<thead></thead>` 表头
  - `<tbody></tbody>` 表体
  - `<tfoot></tfoot>` 表尾
  - `tr, td, th` 表中一行， 一行中的一个单元格， 自带加粗效果单元格
- `<form></form>`
  - `name, value`
  - `<form></form>` 表单项
    - `action (url, r_path, a_path)`
    - `method (get, post, put, delete, option)`
    - `<input ../>`
      - `type (text, password, submit, reset...), name, value, checked, readonly, disabled`
    - `<textarea></textarea>`
    - `<select></select>`
      - `<option></option>`
      - `selected`

### page layout
- `<div></div>`
- `<span></span>`

### notes
```html
<!--
            <h1> 标题
            <br> 换行
            <hr> 水平线
            
            列表
                <ol> 有序列表
                <ul> 无序列表
                <li> 列表项
            
            超链接 <a></a> 有两个属性：
                    1. href 定义要跳转的目标资源地址
                        1) 完整url www.baidu.com
                        2) 相对路径
                        3) 绝对路径
                    2. target 定义目标资源打开方式
                        1) _self 当前窗口打开
                        2) _blank 新窗口打开
            
            图像 <img ..attrs.. />
                    1. src 定义图片路径
                        1) url
                        2) 相对路径
                        3) 绝对路径
                    2. title 定义鼠标悬停在图片上时候显示的文字
                    3. alt 定义图片加载失败时候的提示文字
                    4. width height 定义为像素或百分比

                    更精细的格式控制可以通过 CSS 实现

            表格标签
                    table 整张表格
                        thead 表头
                        tbody 表体
                        tfoot 表尾
                            tr 表格中一行
                                td 行中的一个单元格
                                th 自带加粗效果的td
                                    colspan="x" 横向占用x个单元格
                                    rowspan="x" 纵向占用x个单元格
                
            表单标签 form （可以让用户在界面上输入各种信息并提交的一种标签，是向服务器发送数据主要的方式之一）
                    
                    name: 表单项一定要定义name属性，定义提交 时的参数名（key）       
                    value: 表单项还需要定义value属性，定义提交时的实参值（value）

                    form 标签，内部定义用于让用户输入信息的 ‘表单项标签’
                        action: form-attr，定义信息提交的服务器地址 （url， 相对路径， 绝对路径）
                        method: form-attr， 定义信息提交方式 （GET， POST）
                            get: 
                                get 方式， 数据会加在 url 后，以为 ? 作为参数开始表示，多个参数使用 & 隔开
                                    url?key=value&key=value&...
                                特点：
                                    get提交会显示明文，直接暴露在地址栏，不安全
                                    地址栏显示内容长度有限，可提交数据量有限制
                                    地址栏get明文提交只能提交文字

                            post: 
                                post 方式， 数据会通过请求体发送，不会加在 url后面
                                特点：
                                    参数默认不会放到 url 后面
                                    数据不会直接暴露在地址栏上，相对安全（网络数据包可抓，并不绝对安全）
                                    数据是单独打包通过请求体发送的（请求体容量很大，可以提交大量数据）
                                    请求体中数据可以是字符、字节数据、文件

            
                    input 标签， 主要的表单项标签，用于定义表单项
                        name: input-attr， 定义提交的参数名
                        type: input-attr， 定义表单项类型
                            text
                            password
                            submit
                            reset
                            radio: 单选框， 多个单选框使用相同name属性值时，就会有互斥效果
                            checkbox: 复选框，多个选项
                            hidden: 隐藏域， 不显示在页面上，但是会一起被提交。希望用户提交特定信息，为了避免数据被修改，设置为隐藏域信息  
                            file: 上传文件    
                        value attr
                        checked: 表明默认选项 attr
                        readonly: 只读选项 attr
                        disabled: 使input选项失效 attr
                    
                    textarea 标签，多行文本框
                    select 下拉框
                        option: 定义选项
                        selected: 标记默认显示的选项，和checked本质相同

                    
        
        -->
```
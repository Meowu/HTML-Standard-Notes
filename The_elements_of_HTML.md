## The elements of HTML

#### The document element
* 开始和闭合标签可以省略如果其第一个子元素或者紧跟着的元素不是一个 `comment` 节点。
* 作者应该在根 `html` 元素上指定 `lang` 属性。能够帮助语音合成工具使用何种发音或者翻译工具使用什么规则等等。


#### Document metadata

##### The head element
`head` 元素代表了 `Document` 的 `metadata` 的集合。它不属于任何分类。
`title` 元素绝大多数情况下是必须的。
```html
    <!DOCTYPE HTML>
    <HTML LANG="EN">
    <HEAD>
        <META CHARSET="UTF-8">
        <BASE HREF="https://www.example.com/">
        <TITLE>An application with a long head</TITLE>
        <LINK REL="STYLESHEET" HREF="default.css">
        <LINK REL="STYLESHEET ALTERNATE" HREF="big.css" TITLE="Big Text">
        <SCRIPT SRC="support.js"></SCRIPT>
        <META NAME="APPLICATION-NAME" CONTENT="Long headed application">
    </HEAD>
    <BODY>
    ...
```
##### The base element
放在 `head` 元素内部，只有同时存在一个，没有结束标签。且必须放在所有包含 `url` 的元素前。
仅作为全局相对路径 `URL` 的 `base URL` 。

##### The link element
HTML 中 <link> 元素指定了外部资源与当前文档的关系。 这个元素的用途包括为导航定义一个关系框架。这个元素经常用来链接样式表（如CSS文件）。
**attributes**
* href — Address of the hyperlink p270
* crossorigin — How the element handles crossorigin requests
* rel — Relationship between the document containing the hyperlink p270 and the destination resource
* media — Applicable media
* integrity — Integrity metadata used in Subresource Integrity checks [SRI]p1215
* hreflang — Language of the linked resource
* type — Hint for the type of the referenced resource
* referrerpolicy — Referrer policy for fetches initiated by the element
* sizes — Sizes of the icons (for rel="icon") 浏览器使用根据该值来决定使用哪个 icon 。如果一个 `link` 元素没有通过 `rel` 属性指定了 `icon` 或者 `apple-touch-icon` 时不能使用该属性。
    ```html
    <link rel="apple-touch-icon" sizes="120x120" href="/public/logo-120.png">
    ```

* as — Potential destination for a preload request (for rel="preload" and rel="modulepreload") 当 `rel` 属性指定这两个关键字时使用。例如当 `href` 是一个脚本时， `as="script"` 。它指定了<link>所加载的内容的类型，对于内容的优先级、请求匹配、正确的内容安全策略的选择以及正确的 Accept请求头的设置，这个属性是必需的。
* color — Color to use when customizing a site's icon (仅当 rel="mask-icon" 时使用。)
* Also, the title attribute has special semantics on this element: Title of the link; CSS style sheet set name. `link` 标签的 `title` 属性跟全局 `title` 属性不同的是当没有该属性时，它就是空，不会继承父元素的 `title` 。

必须通过 `href` 属性指定一个 `URL` ，否则该元素无效。`rel` 和 `itemprop` 必须且只能指定一个。
必须指定 `rel` 属性，否则链接无效。且只能指定以下值：
1. alternate
2. dns-prefetch
3. icon
4. modulepreload
5. next
6. pingback
7. preconnect
8. prefetch
9. preload
10. prerender
11. search
12. stylesheet

处理 `type` 属性：
```html
If a document contains style sheet links labeled as follows:
<link rel="stylesheet" href="A" type="text/plain">
<link rel="stylesheet" href="B" type="text/css">
<link rel="stylesheet" href="C">
...then a compliant UA that supported only CSS style sheets would fetch the B and C files, and skip the A file (since text/plain is
not the MIME type for CSS style sheets).
For files B and C, it would then check the actual types returned by the server. For those that are sent as text/cssp1206, it would
apply the styles, but for those labeled as text/plain, or any other type, it would not.
If one of the two files was returned without a Content-Typep87 metadata, or with a syntactically incorrect type like ContentType:
"null", then the default type for stylesheetp290 links would kick in. Since that default type is text/cssp1206, the style sheet
would nonetheless be applied.
```



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
```html
<base href="http://www.example.com/">
<base target="_blank" href="http://www.example.com/">
```

##### The link element
HTML 中 <link> 元素指定了外部资源与当前文档的关系。 这个元素的用途包括为导航定义一个关系框架。这个元素经常用来链接样式表（如CSS文件）。
**attributes**
使用 `link` 元素可以创建两种类型的链接：内部资源和超链接。创建了多少个链接取决于 `rel` 元素指定的关键字。
* href — Address of the hyperlink p270
* crossorigin — How the element handles crossorigin requests 此枚举属性指定在加载相关图片时是否必须使用 CORS. 启用 `CORS` 的图片 可以在 `<canvas>` 元素中使用, 并避免其被污染。有 `anonymous` 和 `use-credential` 两种值。
* rel — Relationship between the document containing the hyperlink and the destination resource
* media — Applicable media
* integrity — Integrity metadata used in Subresource Integrity checks [SRI]p1215
* hreflang — Language of the linked resource
* type — Hint for the type of the referenced resource
* referrerpolicy — Referrer policy for fetches initiated by the element
* sizes — Sizes of the icons (for rel="icon") 浏览器使用根据该值来决定使用哪个 icon 。如果一个 `link` 元素没有通过 `rel` 属性指定了 `icon` 或者 `apple-touch-icon` 时不能使用该属性。
    ```html
    <link rel="apple-touch-icon" sizes="120x120" href="/public/logo-120.png">
    ```

`rel` 指定为 `stylesheet` 的时候默认类型是 `text/css` 。

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


##### The meta element
属于 `Metadata content` 类型，通常出现在 `head` 元素内。如果指定了 `itemprop` 属性，也可以是 `flow content` 或者 `phrasing content` ，此时就可以出现在对应的 `context` 下。没有结束标签。

内容属性：`name` `http-equiv` `content` `charset` 以及其它全局属性。
该元素表示了那些 `title` `base` `link` `style` `script` 元素无法表达的内容。
> The meta element can represent document-level metadata with the **`name`** attribute, pragma directives with the **`http-equiv`** attribute, and the file's character encoding declaration when an HTML document is serialized to string form (e.g. for transmission over the network or for disk storage) with the **`charset`** attribute.

内容属性：
* 全局属性
* name
* http-equiv
* content
* charset

* `name` `http-equiv` `itemprop` `charset` 属性必须指定且只能指定一个。当指定了 `name` `http-equiv` `itemprop` 时， `content` 属性也必须被指定，否则会被忽略。每个文档只能有一个包含 `charset` 属性的 `meta` 元素。

###### Standard metadata names
一些 `meta` 元素 `name` 属性能够指定的合法值。
1. application-name 如果当前页是一个 Web 应用，则指定该属性。
2. author
3. description 页面描述。每页最多一个包含该属性的 `meta` 元素。
4. generator 指定文档是由哪种软件生成的。 `<meta name=generator content="Frontweaver 8.2">` 。
5. keywords 页面关键字，由逗号分隔开。许多搜索引擎并不考虑这些关键字，因为可能会被用来误导搜索引擎从而导致不准确的结果。
6. referrer 指定 `referrer policy` 。
7. theme-color 指定一个建议的颜色用来给浏览器显示页面。最多只有一个包含该属性的 `meta` 元素。`<meta name="theme-color" content="#3c790a">`
8. 其它。任何人都可以定义自己的 metadata names 集合。不需要注册这些扩展。但是要注意不能跟已有的重复。

###### Pragma directives
当 `meta` 元素指定了 `http-equiv` 属性，该元素成为一个编译指示指令。
下表定义了该属性的关键字：
| State | Keyword | Notes |
| ----- | ------- | ----- |
| Content Language | content-language | Non-conforming |
| Encoding declaration | content-type |                |
| Default style | default-style |                      |
| Refresh       | refresh |             |
| Set-Cookie | set-cookie | Non-conforming |
| X-UA-Compatible | x-ua-compatible | |
| Content security policy | content-security-policy | |



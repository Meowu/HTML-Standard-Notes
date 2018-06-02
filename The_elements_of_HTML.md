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
使用 `link` 元素可以创建两种类型的链接：内部资源和超链接。创建了多少个链接取决于 `rel` 元素指定的关键字。
** attributes **
* href — Address of the hyperlink p270
* crossorigin — How the element handles crossorigin requests 此枚举属性指定在加载相关图片时是否必须使用 CORS. 启用 `CORS` 的图片 可以在 `<canvas>` 元素中使用, 并避免其被污染。有 `anonymous` 和 `use-credential` 两种值。
* rel — Relationship between the document containing the hyperlink and the destination resource
* media — Applicable media
* integrity — Integrity metadata used in Subresource Integrity checks [SRI]p1215
* hreflang — Language of the linked resource
* type — Hint for the type of the referenced resource
* referrerpolicy — Referrer policy for fetches initiated by the element
* sizes — Sizes of the icons (for relp152="iconp284")
* as — Potential destination for a preload request (for relp152="preloadp289" and relp152="modulepreloadp286")
* color — Color to use when customizing a site's icon (for relp152="mask-icon")
* Also, the title attribute has special semantics p153 on this element: Title of the link; CSS style sheet set name.

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

`rel` 指定为 `stylesheet` 的时候默认类型是 `text/css` 。

##### The meta element
属于 `Metadata content` 类型，通常出现在 `head` 元素内。如果指定了 `itemprop` 属性，也可以是 `flow content` 或者 `phrasing content` ，此时就可以出现在对应的 `context` 下。没有结束标签。

内容属性：`name` `http-equiv` `content` `charset` 以及其它全局属性。


## The elements of HTML

#### The document element
* 开始和闭合标签可以省略如果其第一个子元素或者紧跟着的元素不是一个 `comment` 节点。
* 作者应该在根 `html` 元素上指定 `lang` 属性。能够帮助语音合成工具使用何种发音或者翻译工具使用什么规则等等。


#### Document metadata

###### The head element
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
###### The base element
放在 `head` 元素内部，只有同时存在一个，没有结束标签。且必须放在所有包含 `url` 的元素前。
仅作为全局相对路径 `URL` 的 `base URL` 。

###### The link element
** attributes **
* href — Address of the hyperlink p270
* crossorigin — How the element handles crossorigin requests
* rel — Relationship between the document containing the hyperlink p270 and the destination resource
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


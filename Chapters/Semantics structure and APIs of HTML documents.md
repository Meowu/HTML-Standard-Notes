# Semantics, structure, and APIs of HTML documents

## Documents

每个 XML 或者 HTML 文档在一个 UA 中都表示为一个 `Document` 对象。

`WHATWG DOM standard` 定义了 `Document` 对象的 `URL`。当 `Document` 初始化时被设置，但是在文档的整个生命周期中可能会改变，例如用户 `navigates` 到页面上的 `fragment` ，或者使用一个新的 `URL` 调用 `pushState` 方法。

`createDocument(XML)` 和 `createHTMLDocument(HTML)` 方法创建的文档会立即加载完毕。可以显示设置其 `referer` ，否则为空。

`document.open()` 方法跟 `window.open()` 方法不一样，前者是打开文档写入流，用于重写文档或者追加内容，后者是打开一个新的页面。不过 `document . open( url, name, features )` 的功能类似于 `window.open()` 。

#### Document Object
Document 有三种状态 (readyState)： `loading` `interactive` `complete` 。 当状态发生变化时，会触发 `onreadystatechange` 事件。在已经过渡到 `interactive` 但是尚未过渡到 `complete` 之前会触发 `DOMContentLoaded` 事件，此时除了 `async script` 脚本之外，所有的子资源已经加载完成。

`document.body` 返回 文档的 `body` 元素，或者一个 `frameset` 元素，或者 `null` 。设置值同样必须只能是 `body` 或者 `frameset` ，否则会 throw 。

## Elements
> HTML conveys meaning, rather than presentation.

#### Element 定义
1. Categories（一个元素可能会属于多种类型）
    * Metadata content ( `base` `link` `meta` `noscript` `script` `title` `style` `template` )
        元数据内容设定其它内容的外观或者行为，或者设置文档与其它文档的信息，又或者传递其它文档外的信息。
    * Flow content p126
        body 中的绝大多数元素都被归类为流内容。
    * Sectioning content p126 ( `article` `aside` `nav` `section` )
        定义了 `heading` 和 `footer` 的作用域。每个章节内容都有一个 `heading` 和 `outline` 。
    * Heading content p126
        h1, h2, h3, h4, h5, h6, hgroup
    * Phrasing content p127
        段落内容，也即那些行内元素。只能包含 `phrasing content`, 不能包含 `flow content` 。
    * Embedded content p127
        `audio` `canvas` `video` `iframe` `picture` `object` `svg` `MathML` `img` 
    * Interactive content p127
        顾名思义，用于用户交互。 `a` `href` `iframe` `input` 等等。 `tabindex` 属性可以让任何元素成为可交互的内容。
    * Palpable content
        指的是非空的内容。至少有非空的文本，并且没有 `hidden` 属性，或者可以听到声音，看到图像等等。
2. Contexts in which this element can be used
3. Content model
    * 一个元素期望的内容。也就是在 `DOM` 中它的子节点。
    * 元素间的空白文本节点、注释节点、 `Inter-element whitespace` 以及 `processing instruction nodes` 在解析时会被也应该被忽略。
    * 创建一个 `td` 节点并将其储存在变量中是符合规范的，虽然它只被允许在 `tr` 元素内使用。此时它属于孤立节点。
4. Tag omission in text/html
5. Content attributes
    * 除了特别说明，属性值都是字符串（空字符），对指定的文本内容没有限制。
6. DOM interface
#### 全局属性
* `WHATWG DOM standard` 为所有的 `HTML` 元素定义了 `class` `id` `slot` 属性。
* To enable assistive technology products to expose a more fine-grained interface than is otherwise possible with HTML elements and attributes, `a set of annotations for assistive technology products` p145 can be specified (the ARIA `role` and `aria-*` attributes).
1. `title` 属性：一个 tooltip 显示元素的指示信息。目前依赖这个属性并不好，因为它需要鼠标指针才会显示 tooltip ，而键盘设备或者触屏无法触发指示信息。如果没有指定该属性，会显示父节点的 title .
2. Custom data attributes `data-*` : are intended to store custom data, state, annotations, and similar, private to the page or application, for
which there are no more appropriate attributes or elements.每个元素都可以包含任意数量的定制属性并且包含任意值。 `element.dataset` 返回一个 `DOMStringMap` 对象。
3. `translate` 被用来规定对应元素的属性值及其子文本节点内容，是否跟随系统语言作出对应的翻译变化。只有 `yes` 或者 `no` 两个值。

#### innerText 属性
1. 当获取元素的 `innerText` 时，如果元素还没被渲染，则返回它的 `textContent` 。
2. 如果已经被渲染，则那些还没被渲染出来的子元素的 `textContent` 会被忽略。
3. `textarea` `input` `video` 这些可替换元素不会被 CSS 渲染。
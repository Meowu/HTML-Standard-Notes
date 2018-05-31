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


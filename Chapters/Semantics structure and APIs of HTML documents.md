# Document

每个 XML 或者 HTML 文档在一个 UA 中都表示为一个 `Document` 对象。

`WHATWG DOM standard` 定义了 `Document` 对象的 `URL`。当 `Document` 初始化时被设置，但是在文档的整个生命周期中可能会改变，例如用户 `navigates` 到页面上的 `fragment` ，或者使用一个新的 `URL` 调用 `pushState` 方法。


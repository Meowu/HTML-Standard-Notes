# User Interaction
所有的 HTML 元素都可以有一个 `hidden` 属性，它的值是 `boolean` 。当指定了 `hidden` 属性，浏览器不会渲染它，通常这是通过样式来实现的。所以我们可以使用样式覆盖它， `display: block` 就可以取消隐藏。如果需要隐藏某个元素的时候，必须注意其样式。当然也可以通过 JS 动态改变 `hidden` 的值。

被设置了 `hidden` 属性的内容不会被读屏器所知道。
非 `hidden` 的元素不要链接到隐藏元素， `label` 的 `for` 属性也不要引用 `hidden` 的元素。
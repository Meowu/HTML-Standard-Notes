# Introduction

## Privacy concerns

一些可以被用来对用户进行特征提取的信息：

1. IP 地址。
2. canvas 绘制文本（用户安装了哪些字体）
3. Cookies
4. The exact list of which features a user agents supports.
5. The maximum allowed stack depth for recursion in script.
6. Features that describe the user's environment, like Media Queries and the Screen object. 
7. The user's time zone.

## Cross-site 沟通

`postMessage()` api 提供了一种让两个网站可以直接沟通的机制。虽然看上去这似乎会导致隐私问题，事实上比这个 api 更早的特性同样可以实现相同的功能：比如 `iframe` `cross-site image request` 以及上述的特诊提取技术等等。

Fundamentally, users that do not trust a site to treat their information with respect have to avoid visiting that site at all.

## Qucik start

HTMl 标签的属性值其实可以不用引号包起来，只要它不包含 `ASCII whitespace` 或者   `" ' ` = < >  其中任何一个。`

浏览器会把文档中的 html 标记语言解析成一个 DOM 树：

![](https://www.notion.so/file/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fb0f944f6-3863-4c80-b331-87b71f8113f6%2FUntitled)

Each element in the `DOM` tree is represented by an object, and these objects have APIs so that they can be manipulated.

![](https://www.notion.so/file/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F7272b206-fa52-443c-b276-b0c615cf6fdb%2FUntitled)
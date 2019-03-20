---
title: 'Data URLs 嵌入文件'
date: 2019-03-20T10:58:56+08:00
categories: ['data']
tags: ['html']
description: 'Data URLs，即前缀为 data: 协议的的URL，其允许内容创建者向文档中嵌入小文件。'
css: ['/file-css/2019-3/data.css', '/css/main.css']
draft: false
---

| 来源                                                                       | 收录日期  |
| -------------------------------------------------------------------------- | --------- |
| [MDN:mozilla](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/data_URIs) | 2019.3.20 |

**Data URLs**，即前缀为 `data:`  协议的的 URL，其允许内容创建者向文档中嵌入小文件。

## 先试试，不甜不给钱

### css 方式

<img class="data-img-trangle" >

> 该图片的 Css 格式，

```css
.data-img-trangle {
  border: 5px dashed blue;
  width: 100%;
  height: 30vh;
  background: url('data:image/png;base64,iVBORw0KGg...');
}
```

> 注意 ⚠️，这种方式一开始与`src方式`最大的不同，是这个 img 元素并没有被图片撑起来。
> 下面的`<svg>`是写入`img`元素的，也就是，从一开始就拥有了图片，而`css方式`，一开始是没有图片的(支撑)。

这也导致。若是没有定义`width`+`height`，img 元素就只是一个小点。如下:

<img class="data-img-trangle-without-xy" >

这个蓝点的 css

```css
.data-img-trangle-without-xy {
  border: 5px dashed blue;
  /* 没有了width+height，也没有其他预先规范css */
  background: url('data:image/png;base64,iVBORw0KGg...');
}
```

### src 方式

```html
<img
  src='data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" id="Layer_1" x="0px" y="0px" viewBox="0 0 100 100" enable-background="new 0 0 100 100" xml:space="preserve" height="100px" width="100px">
<g>
    <path d="M28.1,36.6c4.6,1.9,12.2,1.6,20.9,1.1c8.9-0.4,19-0.9,28.9,0.9c6.3,1.2,11.9,3.1,16.8,6c-1.5-12.2-7.9-23.7-18.6-31.3   c-4.9-0.2-9.9,0.3-14.8,1.4C47.8,17.9,36.2,25.6,28.1,36.6z"/>
    <path d="M70.3,9.8C57.5,3.4,42.8,3.6,30.5,9.5c-3,6-8.4,19.6-5.3,24.9c8.6-11.7,20.9-19.8,35.2-23.1C63.7,10.5,67,10,70.3,9.8z"/>
    <path d="M16.5,51.3c0.6-1.7,1.2-3.4,2-5.1c-3.8-3.4-7.5-7-11-10.8c-2.1,6.1-2.8,12.5-2.3,18.7C9.6,51.1,13.4,50.2,16.5,51.3z"/>
    <path d="M9,31.6c3.5,3.9,7.2,7.6,11.1,11.1c0.8-1.6,1.7-3.1,2.6-4.6c0.1-0.2,0.3-0.4,0.4-0.6c-2.9-3.3-3.1-9.2-0.6-17.6   c0.8-2.7,1.8-5.3,2.7-7.4c-5.2,3.4-9.8,8-13.3,13.7C10.8,27.9,9.8,29.7,9,31.6z"/>
    <path d="M15.4,54.7c-2.6-1-6.1,0.7-9.7,3.4c1.2,6.6,3.9,13,8,18.5C13,69.3,13.5,61.8,15.4,54.7z"/>
    <path d="M39.8,57.6C54.3,66.7,70,73,86.5,76.4c0.6-0.8,1.1-1.6,1.7-2.5c4.8-7.7,7-16.3,6.8-24.8c-13.8-9.3-31.3-8.4-45.8-7.7   c-9.5,0.5-17.8,0.9-23.2-1.7c-0.1,0.1-0.2,0.3-0.3,0.4c-1,1.7-2,3.4-2.9,5.1C28.2,49.7,33.8,53.9,39.8,57.6z"/>
    <path d="M26.2,88.2c3.3,2,6.7,3.6,10.2,4.7c-3.5-6.2-6.3-12.6-8.8-18.5c-3.1-7.2-5.8-13.5-9-17.2c-1.9,8-2,16.4-0.3,24.7   C20.6,84.2,23.2,86.3,26.2,88.2z"/>
    <path d="M30.9,73c2.9,6.8,6.1,14.4,10.5,21.2c15.6,3,32-2.3,42.6-14.6C67.7,76,52.2,69.6,37.9,60.7C32,57,26.5,53,21.3,48.6   c-0.6,1.5-1.2,3-1.7,4.6C24.1,57.1,27.3,64.5,30.9,73z"/>
</g>
</svg>'
  alt=""
/>
```

<div class="example">

<img src='data:image/svg+xml;utf8,<svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" id="Layer_1" x="0px" y="0px" viewBox="0 0 100 100" enable-background="new 0 0 100 100" xml:space="preserve" height="100px" width="100px">
<g>
    <path d="M28.1,36.6c4.6,1.9,12.2,1.6,20.9,1.1c8.9-0.4,19-0.9,28.9,0.9c6.3,1.2,11.9,3.1,16.8,6c-1.5-12.2-7.9-23.7-18.6-31.3   c-4.9-0.2-9.9,0.3-14.8,1.4C47.8,17.9,36.2,25.6,28.1,36.6z"/>
    <path d="M70.3,9.8C57.5,3.4,42.8,3.6,30.5,9.5c-3,6-8.4,19.6-5.3,24.9c8.6-11.7,20.9-19.8,35.2-23.1C63.7,10.5,67,10,70.3,9.8z"/>
    <path d="M16.5,51.3c0.6-1.7,1.2-3.4,2-5.1c-3.8-3.4-7.5-7-11-10.8c-2.1,6.1-2.8,12.5-2.3,18.7C9.6,51.1,13.4,50.2,16.5,51.3z"/>
    <path d="M9,31.6c3.5,3.9,7.2,7.6,11.1,11.1c0.8-1.6,1.7-3.1,2.6-4.6c0.1-0.2,0.3-0.4,0.4-0.6c-2.9-3.3-3.1-9.2-0.6-17.6   c0.8-2.7,1.8-5.3,2.7-7.4c-5.2,3.4-9.8,8-13.3,13.7C10.8,27.9,9.8,29.7,9,31.6z"/>
    <path d="M15.4,54.7c-2.6-1-6.1,0.7-9.7,3.4c1.2,6.6,3.9,13,8,18.5C13,69.3,13.5,61.8,15.4,54.7z"/>
    <path d="M39.8,57.6C54.3,66.7,70,73,86.5,76.4c0.6-0.8,1.1-1.6,1.7-2.5c4.8-7.7,7-16.3,6.8-24.8c-13.8-9.3-31.3-8.4-45.8-7.7   c-9.5,0.5-17.8,0.9-23.2-1.7c-0.1,0.1-0.2,0.3-0.3,0.4c-1,1.7-2,3.4-2.9,5.1C28.2,49.7,33.8,53.9,39.8,57.6z"/>
    <path d="M26.2,88.2c3.3,2,6.7,3.6,10.2,4.7c-3.5-6.2-6.3-12.6-8.8-18.5c-3.1-7.2-5.8-13.5-9-17.2c-1.9,8-2,16.4-0.3,24.7   C20.6,84.2,23.2,86.3,26.2,88.2z"/>
    <path d="M30.9,73c2.9,6.8,6.1,14.4,10.5,21.2c15.6,3,32-2.3,42.6-14.6C67.7,76,52.2,69.6,37.9,60.7C32,57,26.5,53,21.3,48.6   c-0.6,1.5-1.2,3-1.7,4.6C24.1,57.1,27.3,64.5,30.9,73z"/>
</g>
</svg>' alt="" />

</div>

## 目录

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [语法](#%E8%AF%AD%E6%B3%95)
- [给数据作 base64 编码](#%E7%BB%99%E6%95%B0%E6%8D%AE%E4%BD%9C-base64-%E7%BC%96%E7%A0%81)
  - [在网页上使用 JavaScript](#%E5%9C%A8%E7%BD%91%E9%A1%B5%E4%B8%8A%E4%BD%BF%E7%94%A8-javascript)
- [常见问题](#%E5%B8%B8%E8%A7%81%E9%97%AE%E9%A2%98)
  - [语法](#%E8%AF%AD%E6%B3%95-1)
  - [HTML 代码格式化](#html-%E4%BB%A3%E7%A0%81%E6%A0%BC%E5%BC%8F%E5%8C%96)
  - [长度限制](#%E9%95%BF%E5%BA%A6%E9%99%90%E5%88%B6)
  - [缺乏错误处理](#%E7%BC%BA%E4%B9%8F%E9%94%99%E8%AF%AF%E5%A4%84%E7%90%86)
  - [不支持查询字符串](#%E4%B8%8D%E6%94%AF%E6%8C%81%E6%9F%A5%E8%AF%A2%E5%AD%97%E7%AC%A6%E4%B8%B2)
- [延展](#%E5%BB%B6%E5%B1%95)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## 语法

Data URLs 由四个部分组成：前缀(`data:`)、指示数据类型的 MIME 类型、如果非文本则为可选的`base64`标记、数据本身：

```
data:[<mediatype>][;base64],<data>
```

`mediatype`是个 MIME 类型的字符串，例如 "`image/jpeg`" 表示  JPEG 图像文件。如果被省略，则默认值为  `text/plain;charset=US-ASCII`

如果数据是文本类型，你可以直接将文本嵌入  (根据文档类型，使用合适的实体字符或转义字符)。如果是二进制数据，你可以将数据进行 base64 编码之后再进行嵌入。

下面是一些示例：

`data:,Hello%2C%20World!`

简单的 text/plain 类型数据

`data:text/plain;base64,SGVsbG8sIFdvcmxkIQ%3D%3D`

上一条示例的 base64 编码版本

`data:text/html,%3Ch1%3EHello%2C%20World!%3C%2Fh1%3E`

一个 HTML 文档源代码 `<h1>Hello, World</h1>`

`data:text/html,<script>alert('hi');</script>`

一个会执行 JavaScript alert 的  HTML 文档。注意 script 标签必须封闭。

## 给数据作 base64 编码

在 Linux 或者 Mac OS 系统上，你可以使用 `uuencode`命令行工具来简单实现编码：

```bash
uuencode -m `infile` `remotename`
```

`infile`  参数表示要作 base64 编码的文件名称，`remotename`  参数表示输出的文件名称, 实际上并没有在  data  方案的 URLs 中使用。

输出结果如下：

```bash
begin-base64 664 test
YSBzbGlnaHRseSBsb25nZXIgdGVzdCBmb3IgdGV2ZXIK
====
```

以上 Data URL 会使用位于首行之后的编码后的数据

### 在网页上使用 JavaScript

Web APIs 已经有对 base64 进行编码解码的方法: [Base64 encoding and decoding](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Base64_encoding_and_decoding).

## 常见问题

下文介绍一些在使用`data` URIs 时遇到的常见问题:

### 语法

`data` URLs 的格式很简单，但很容易会忘记把逗号加在 "data" 协议名后面，在对数据进行 base64 编码时也很容易发生错误。

### HTML 代码格式化

一个  `data` URL 是一个文件中的文件，相对于文档来说这个文件可能就非常的长。因为 data URL 也是  URL，所以 data 会用空白符(换行符, 制表符, 空格)来对它进行格式化。但如果数据是经过 base64 编码的，就可能会[遇到一些问题](http://bugzilla.mozilla.org/show_bug.cgi?id=73026#c12 'http://bugzilla.mozilla.org/show_bug.cgi?id=73026#c12')。

### 长度限制

虽然 Firefox 支持无限长度的  `data` URLs，但是标准中并没有规定浏览器必须支持任意长度的  `data` URIs。比如，Opera 11 浏览器限制 URLs 最长为 65535  个字符，这意味着 data URLs 最长为  65529 个字符（如果你使用纯文本 data:, 而不是指定一个 MIME 类型的话，那么 65529 字符长度是编码后的长度，而不是源文件）。

### 缺乏错误处理

MIME 类型错误或者 base64 编码错误,都会造成`data` URIs 无法被正常解析, 但不会有任何相关错误提示.

### 不支持查询字符串

一个 data URI 的数据字段是没有结束标记的,所以尝试在一个 data URI 后面添加查询字符串会导致,查询字符串也一并被当作数据字段.例如:

```
data:text/html,lots of text...<p><a name%3D"bottom">bottom</a>?arg=val
```

这个 data URL 代表的 HTML 源文件内容为:

```
lots of text...<p><a name="bottom">bottom</a>?arg=val
```

## 延展

- [浏览器兼容表格](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/data_URIs#Support_in_other_browsers)
- [图片转义 data URL : online](https://www.base64-image.de/)
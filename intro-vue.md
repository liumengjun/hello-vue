# 初触前端 | VUE入门

## HTML & CSS

> 构建网页的核心技术，

### HTML(Hypertext Markup Language)

> 超文本标记语言，构建网页的内容结构。
> 插曲: `MarkUP`(vs `MarkDown`)，丰富的文字标记，描述网页内容。MarkDown基于已有的规则如HTML，描述网页。

### CSS(Cascading Style Sheets)

> 层叠样式表，描述网页的样式排版。顾名思义，层叠，样式，列表。

### see also:

- https://www.w3.org/standards/webdesign/htmlcss
- https://developer.mozilla.org/zh-CN/docs/Web/Reference

## JavaScript

> 作为开发Web页面的脚本语言而出名，动态改变网页内容
> 现在服务端也可以用JS来编写了, `BigQuery`中UDF也用js编写。

1. JavaScript作为编程语言本身
2. Web APIs, 操作`DOM(Document Object Model)`, 规范js如何与 HTML&CSS 元素交互

### see also:

- https://www.w3.org/standards/webdesign/script
- https://developer.mozilla.org/zh-CN/docs/Web/JavaScript

## 乱象丛生到标准

> 浏览器厂商众多
> 从发展史来看，HTML出现过一些扩展，XML，XHTML，DHTML。HTML2 到 `HTML5`。`W3C`组织维护其标准, 以及CSS。
> JS实现引擎也很多，每家浏览器里的都有些差异。`Google`的`V8`特别出名。`Node.js`出现。
> 出现过各种CSS选择器组件，其中`jQuery`最为出名。
> JS标准是`ECMAScript`, 由`ECMA(European Computer Manufacturers Association)`制定。目前流行的是`ES6(ECMAScript2015)`, `ECMAScript2020`正在制定中。
> `Web APIs`部分依然由`W3C`组织维护。

## demo

> [先看效果](hello-world.js.html)

### hello html

```html
<div id="app" style="color: #FF3640;">
  Hello HTML
</div>
<style>
  #app {
    font-style: italic;
  }
</style>
```

### hello JS

```html
<div id="app-2">
</div>

<script>
  // document.findDocumentById('app-2').innerHtml = "Hello World"
  document.getElementById('app-2').innerHTML = 'Hello JS'
  setTimeout(function() {
    document.getElementById('app-2').innerText = '哈哈😀😀😀!'
  }, 3000)
</script>
```

### hello jQuery

```html
<div id="app-3">
</div>

<script src="https://code.jquery.com/jquery-3.5.1.min.js"></script>
<script>
  $('#app-3').html('Hello JQuery')
  setTimeout(function() {
    $('#app-3').text('😀😀')
  }, 4000)
</script>
```

## VUE前端框架

> 数据控制网页内容，而不是一个字一个字地编写js控制网页内容。
> angular，react等等其他很多框架，便于大家编写web应用。
> cordova，meteor，flutter等等多端框架，web端编写完成后，可直接编译生成PC和手机端APP。
> 得益于标准的推进，动力是需求的提高。

### MVVM 模型

![MVVM 模型](mvvm(Model-View-ViewModel).png)

没有完全遵循 MVVM 模型，但是 Vue 的设计也受到了它的启发。ViewModel 表示 Vue 实例。(MVVM来自MVC模式。)

一个 Vue 应用由一个通过 new Vue 创建的根 Vue 实例，以及可选的嵌套的、可复用的组件树组成。***所有的 Vue 组件都是 Vue 实例。***

当一个 Vue 实例被创建时，它将 data 对象中的所有的 property 加入到 Vue 的响应式系统中。当这些 property 的值发生改变时，视图将会产生“响应”，即匹配更新为新的值。Vue 有完善的[生命周期](https://cn.vuejs.org/v2/guide/instance.html#生命周期图示)和状态管理模式。

### vue demos

> [看效果，代码直接看源文件](hello-vue.html)

### 响应式原理

> 当你把一个普通的 JavaScript 对象传入 Vue 实例作为 data 选项，Vue 将遍历此对象所有的 property，并使用 Object.defineProperty 把这些 property 全部转为 getter/setter。
> 这些 getter/setter 对用户来说是不可见的，但是在内部它们让 Vue 能够追踪依赖，在 property 被访问和修改时通知变更。
> [查看原文](https://cn.vuejs.org/v2/guide/reactivity.html)

## vue 语法

### 模板

使用“Mustache”语法 (双大括号)，显示数据或JS表达式，***vue的属性也是js表达式, 相当于`this.`调用***。
使用 v-html 指令输出真正的 HTML

### 指令

指令 (Directives) 是带有 v- 前缀的特殊标志，值是单个 JavaScript 表达式。

如: v-if, v-for, v-html, v-bind, v-on等，具体看[Vue API](https://cn.vuejs.org/v2/api/#指令)

### 属性 & 事件

使用 v-bind 指令设置属性，缩写为`:`，即一个冒号。
使用 v-on 指令设置事件，缩写为`@`。
普通属性像写原始HTML那样直接写就可以。

## vue 组件

> 所有的 Vue 组件都是 Vue 实例。
> 模板 + Vue 配置选项

`vue demos`中有个简单组件示例。

### 单文件组件

文件扩展名为 `.vue`，便于使用 **``webpack``** 或 ``Browserify`` 等构建工具。

```vue
<template>
  <p>{{ greeting }} World!</p>
</template>

<script>
export default {
  data: function() {
    return {
      greeting: "Hello"
    };
  }
}
</script>

<style scoped>
p {
  font-size: 2em;
  text-align: center;
}
</style>
```

## CSS 补充

> 传统CSS，层级难以控制，不支持变量等。因此诞生了许多增强的CSS编译工具。原始HTML网页中不能直接用，需要借助构建工具。

- [SCSS/SASS](https://sass-lang.com/)
- [less](http://lesscss.org/)
- [stylus](https://stylus-lang.com/)
- [PostCSS](https://postcss.org/)

```html
<style lang="scss" scoped>
p {
    background: red;
    a {
        color: green;
    }
}
</style>
```

## 其他

vue已经发展的非常强大，还有过滤器，支持自定义指令，插件，可复用性强。
生态系统也非常完善，还有`路由`，`状态管理`，`服务端渲染`等功能，能够写出非常庞大的web应用。
能力有限，不再叙述了，请到[vue网站](https://cn.vuejs.org/)学习。

- https://cn.vuejs.org/

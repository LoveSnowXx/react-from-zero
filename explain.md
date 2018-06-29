## 从零开始的React

我比较喜欢 `md` 格式

### 课题

<!-- START doctoc -->
<!-- END doctoc -->

<details>

<summary> ➡️ <strong>0 -  Object Elements/React元素长什么样 </strong> <kbd>课堂开课啦</kbd> </summary>

``` html
<!doctype html>

<title>00 Object Elements/React元素长什么样 - React From Zero</title>

<script src="https://cdn.bootcss.com/react/16.4.0/umd/react.development.js"></script>
<script src="https://cdn.bootcss.com/react-dom/16.4.0-alpha.0911da3/umd/react-dom.development.js"></script>

<div id="app">
```
   
>  我们 React 应用渲染的目标元素 id="app"


``` html
</div>
<script>
```

> `React`使用`ES2015`符号`"tag"`标签化它的元素对象. 

>  它在旧版浏览器上使用 神奇的数字 作为回调. 

``` js
  var magicValue = (Symbol && Symbol.for("react.element")) || 0xeac
```

> `React`使用虚拟`DOM`元素,在渲染时会成为真实的`DOM`的元素. 

> 虚拟`DOM`元素可以被定义为一个简单的对象文字. 

> 通常你会使用`React.createElement()`创建一个元素. 

> 下面看起来就像是`React.createElement()`运行后的返回值.

``` js
  var reactElement = {
```

> 这个特殊的 财产-property 将被`React`检查,

> 确保这个对象是一个`React`元素,

> 而不仅仅是一些用户数据

> `React.createElement()`自动为你设置

``` js

    $$typeof: magicValue,
```

> 我们稍后将讨论 引用-ref ,这也将被`React`检查.

> 但如果您不使用它们,则必须将其设置为null,而不是 未定义-undefined 的 

``` js
    ref: null,
```

> 这定义了 HTML 标签

``` js
    type: "h1",
```

> 这定义了传递给元素的属性

``` js
    props: {
```

> 在这个例子中,只有一个文本节点作为子节点

``` js
      children: "Hello, world!",
```

> 一个`CSS`类

``` js
      className: "abc",
```

> 样式可以作为对象传递, 

> `React`使用 驼峰 而不是虚线 (例如`CSS/D3`) : text-align{虚线} => textAlign{驼峰}

``` js
      style: {
        textAlign: "center",
      },
```

> 事件处理程序也可以作为属性添加,

> `React` 组合自身与浏览器事件,基本上试图规范化浏览器的行为

``` js
      onClick: function (notYourRegularEvent) { alert("click") },
    },

  }
```

> 另一个没有太多配置的元素

``` js
  var anotherElement = {
    $$typeof: magicValue,
    ref: null,
    type: "p",
    props: {
      children: "A nice text paragraph.",
    },
  }
```

> `React`需要一个`DOM`元素作为渲染目标

``` js
  var renderTarget = document.getElementById("app")
```

> `ReactDOM`负责将元素插入到 DOM 中

``` html
  ReactDOM.render(reactElement, renderTarget)
</script>
```

### 完整示例

``` html
<!doctype html>

<title>00 Object Elements/React元素长什么样 - React From Zero</title>

<script src="https://cdn.bootcss.com/react/16.4.0/umd/react.development.js"></script>
<script src="https://cdn.bootcss.com/react-dom/16.4.0-alpha.0911da3/umd/react-dom.development.js"></script>

<div id="app">
  <!--我们 React 应用渲染的目标元素 id="app"-->
</div>

<script>
  var magicValue = (Symbol && Symbol.for("react.element")) || 0xeac7

  var reactElement = {

    $$typeof: magicValue,

    ref: null,

    type: "h1",

    props: {
  
      children: "Hello, world!",
  
      className: "abc",
  
      style: {
        textAlign: "center",
      },
  
      onClick: function (notYourRegularEvent) { alert("click") },
    },
  }

  var anotherElement = {
    $$typeof: magicValue,
    ref: null,
    type: "p",
    props: {
      children: "A nice text paragraph.",
    },
  }

  var renderTarget = document.getElementById("app")

  ReactDOM.render(reactElement, renderTarget)
</script>
```


</details>

---

<details>

<summary> ➡️ <strong>1 -  Element Factory</strong> <kbd>课堂开课啦</kbd> </summary>


</details>

---

<details>

<summary> ➡️ <strong>2 -  JSX</strong> <kbd>课堂开课啦</kbd> </summary>


</details>

---

<details>

<summary> ➡️ <strong>3 -  Nested Elements</strong> <kbd>课堂开课啦</kbd> </summary>


</details>

---

<details>

<summary> ➡️ <strong>4 -  Components</strong> <kbd>课堂开课啦</kbd> </summary>


</details>

---

<details>

<summary> ➡️ <strong>5 -  Properties</strong> <kbd>课堂开课啦</kbd> </summary>


</details>

---

<details>

<summary> ➡️ <strong>6 -  Property Types</strong> <kbd>课堂开课啦</kbd> </summary>


</details>

---

<details>

<summary> ➡️ <strong>7 -  Property Example</strong> <kbd>课堂开课啦</kbd> </summary>


</details>

---

<details>

<summary> ➡️ <strong>8 -  Nested Components</strong> <kbd>课堂开课啦</kbd> </summary>


</details>

---

<details>

<summary> ➡️ <strong>9 -  Component Classes</strong> <kbd>课堂开课啦</kbd> </summary>


</details>

---

<details>

<summary> ➡️ <strong>10  - Example App</strong> <kbd>课堂开课啦</kbd> </summary>


</details>

---

<details>

<summary> ➡️ <strong>11  - Lifecycle Methods</strong> <kbd>课堂开课啦</kbd> </summary>


</details>

---

<details>

<summary> ➡️ <strong>12  - Component refactor</strong> <kbd>课堂开课啦</kbd> </summary>


</details>

---

<details>

<summary> ➡️ <strong>13  - Element Refactor</strong> <kbd>课堂开课啦</kbd> </summary>


</details>

---

<details>

<summary> ➡️ <strong>14  - References</strong> <kbd>课堂开课啦</kbd> </summary>


</details>

---

<details>

<summary> ➡️ <strong>15  - Simple Integration</strong> <kbd>课堂开课啦</kbd> </summary>


</details>

---

<details>

<summary> ➡️ <strong>16  - Advanced Integration</strong> <kbd>课堂开课啦</kbd> </summary>


</details>

---

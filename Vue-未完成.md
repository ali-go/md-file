## Vue的知识注意点

#### 1、具名插槽

自vue2.6版本之后不允许使用**slot=”插槽名“**的写法，并且不能直接写在标签上，如下是2.6之前的具名插槽写法：

```js
（1）、写在template上
<base-layout>
  <template slot="header">
    <h1>Here might be a page title</h1>
  </template>

  <p>A paragraph for the main content.</p>
  <p>And another one.</p>

  <template slot="footer">
    <p>Here's some contact info</p>
  </template>
</base-layout>

（2）、写在标签上
<base-layout>
  <h1 slot="header">Here might be a page title</h1>

  <p>A paragraph for the main content.</p>
  <p>And another one.</p>

  <p slot="footer">Here's some contact info</p>
</base-layout>
```

上面方法2.6版本前可以，之后具名插槽必须用下面写法：

```js
子组件内
<div class="container">
  <header>
    <slot name="header"></slot>
  </header>
  <main>
    <slot></slot>
  </main>
  <footer>
    <slot name="footer"></slot>
  </footer>
</div>
//一个不带 name 的 <slot> 出口会带有隐含的名字“default”。

调用组件
<base-layout>
  <template v-slot:header>
    <h1>Here might be a page title</h1>
  </template>

  <p>A paragraph for the main content.</p>
  <p>And another one.</p>
//上面直接写两个的p标签插入默认插槽，也可以写成下面这种写法：
  //<template v-slot:default>
   // <p>A paragraph for the main content.</p>
   // <p>And another one.</p>
  //</template>

  <template v-slot:footer>
    <p>Here's some contact info</p>
  </template>
</base-layout>
```

现在 `<template>` 元素中的所有内容都将会被传入相应的插槽。任何没有被包裹在带有 `v-slot` 的 `<template>` 中的内容都会被视为默认插槽的内容。

注意 **`v-slot` 只能添加在 `<template>` 上** (只有[一种例外情况](https://cn.vuejs.org/v2/guide/components-slots.html#独占默认插槽的缩写语法))

即：**独占默认插槽的缩写语法**

```js
第一种写法：
<current-user v-slot:default="slotProps">
  {{ slotProps.user.firstName }}
</current-user>

第二种：
<current-user v-slot="slotProps">
  {{ slotProps.user.firstName }}
</current-user>
```

只有独占默认插槽可以写在标签上，其余必须写在template上。

注意默认插槽的缩写语法**不能**和具名插槽混用，因为它会导致作用域不明确，只要出现多个插槽，请始终为*所有的*插槽使用完整的基于 `<template>` 的语法：

#### 2、作用域插槽

带有 `slot-scope` attribute 的作用域插槽，自 2.6.0 起被废弃。

在 `<template>` 上使用特殊的 `slot-scope` attribute，可以接收传递给插槽的 prop。

父组件通过slot-scope接受子组件v-bind传递给slot的prop数据。

这里的 `slot-scope` 声明了被接收的 prop 对象会作为 `slotProps` 变量存在于 `<template>` 作用域中。你可以像命名 JavaScript 函数参数一样随意命名 `slotProps`。

这里的 `slot="default"` 可以被忽略为隐性写法。

```js
<slot-example>
  <template slot="default" slot-scope="slotProps">
    {{ slotProps.msg }}
  </template>
</slot-example
```

`slot-scope` attribute 也可以直接用于非 `<template>` 元素 (包括组件)：

例：

```js
<slot-example>
  <span slot-scope="slotProps">
    {{ slotProps.msg }}
  </span>
</slot-example>
```

`slot-scope` 的值可以接收任何有效的可以出现在函数定义的参数位置上的 JavaScript 表达式。这意味着在支持的环境下 ([单文件组件](https://cn.vuejs.org/v2/guide/single-file-components.html)或[现代浏览器](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment#浏览器兼容))，你也可以在表达式中使用 [ES2015 解构](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment#解构对象)，如下：

```js
<slot-example>
  <span slot-scope="{ msg }">
    {{ msg }}
  </span>
</slot-example>
```

例子组件中发送数据，把数据todos传递给slot的prop中，上面通过slot-scope获取todes数据。

```js
<todo-list v-bind:todos="todos">
  <template slot="todo" slot-scope="{ todo }">
    <span v-if="todo.isComplete">✓</span>
    {{ todo.text }}
  </template>
</todo-list>
```

**注意上述作用域插槽写法2.6起废弃！最新用法如下**

有时让插槽内容能够访问子组件中才有的数据是很有用的。例如，设想一个带有如下模板的 `<current-user>` 组件：

```
<span>
  <slot>{{ user.lastName }}</slot>
</span>
```

我们可能想换掉备用内容，用名而非姓来显示。如下：

```
<current-user>
  {{ user.firstName }}
</current-user>
```

然而上述代码不会正常工作，因为只有 `<current-user>` 组件可以访问到 `user` 而我们提供的内容是在父级渲染的。

为了让 `user` 在父级的插槽内容中可用，我们可以将 `user` 作为 `<slot>` 元素的一个 attribute 绑定上去：

```
<span>
  <slot v-bind:user="user">
    {{ user.lastName }}
  </slot>
</span>
```

绑定在 `<slot>` 元素上的 attribute 被称为**插槽 prop**。现在在父级作用域中，我们可以使用带值的 `v-slot` 来定义我们提供的插槽 prop 的名字：

```
<current-user>
  <template v-slot:default="slotProps">
    {{ slotProps.user.firstName }}
  </template>
</current-user>
```

在这个例子中，我们选择将包含所有插槽 prop 的对象命名为 `slotProps`，但你也可以使用任意你喜欢的名字。

跟 `v-on` 和 `v-bind` 一样，`v-slot` 也有缩写，即把参数之前的所有内容 (`v-slot:`) 替换为字符 `#`。例如 `v-slot:header` 可以被重写为 `#header`：
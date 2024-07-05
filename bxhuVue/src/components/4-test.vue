<!--
我们可以通过 v-if 和 v-for 指令条件性地或循环地渲染内容。
-->

<script setup>
import { ref } from 'vue'

const show = ref(true) // const show = ref(true)：创建一个名为 show 的响应式变量，初始值为 true。用于控制列表的显示和隐藏
const list = ref([1, 2, 3]) // list 的初值是: 1, 2, 3
// 我觉得更好的教程说明应该是list初始化成empty
// const list = ref()

</script>


<!-- 
<ul> (Unordered List)
描述：用于创建一个无序列表，列表项通常使用圆点 (bullet) 标记。

示例：
<ul>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>

解释：上面的代码创建了一个包含三个列表项的无序列表，每个列表项前面都有一个圆点。

<li> (List Item)
描述：用于定义列表中的每一项。可以包含在无序列表 (<ul>) 或有序列表 (<ol>) 中。

示例：
<ul>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>

解释：上面的代码展示了三个列表项 <li>，它们被包含在一个无序列表 <ul> 中。

<p> (Paragraph)
描述：用于定义一个段落。浏览器通常会在段落前后添加一些空白（换行）。

示例：
<p>This is a paragraph.</p>
<p>This is another paragraph.</p>

解释：上面的代码创建了两个段落，每个段落都有一些文本内容 -->


<template>
  <button @click="show = !show">Toggle List</button> 
  <!-- 绑定了一个点击事件，当按钮被点击时，show 的值在 true 和 false 之间切换，控制列表的显示和隐藏 -->
  <button @click="list.push(list.length + 1)">Push Number</button>
  <!-- 绑定了一个点击事件，当按钮被点击时，当前 list 的长度加 1 的值被推入 list 数组的末尾 -->
  <button @click="list.pop()">Pop Number</button>
  <!-- 绑定了一个点击事件，当按钮被点击时，list 数组的最后一个元素被移除 -->
  <button @click="list.reverse()">Reverse List</button>
  <!-- 绑定了一个点击事件，当按钮被点击时，list 数组的元素顺序被反转 -->

  <ul v-if="show && list.length">
    <li v-for="item of list">{{ item }}</li>
  </ul>
  <p v-else-if="list.length">List is not empty, but hidden.</p>
  <p v-else>List is empty.</p>

</template>
<script setup>
const props = defineProps({
  todo: Object
})
</script>

<template>
  <li>Let me have a look at {{ todo.text }}</li>
</template>

<!-- 
defineProps: 使用 defineProps 定义组件的 props，接收一个 todo 对象。

<template> 和 {{ todo.text }}: 在模板部分，使用 <li> 元素显示 todo 对象的 text 属性。 
-->

<!-- 

父组件 (6-test.vue):

定义了一个包含待办事项列表的响应式变量 groceryList。
在模板中使用 v-for 指令遍历 groceryList，为每个待办事项创建一个 TodoItem 组件。
使用 :todo="item" 将当前待办事项对象作为 todo 属性传递给 TodoItem 组件。
使用 :key="item.id" 为每个待办事项设置唯一的 key 属性，帮助 Vue 高效地追踪和更新列表项。


子组件 (TodoItem.vue):

使用 defineProps 定义 todo 属性，接收父组件传递的待办事项对象。
在模板中使用 {{ todo.text }} 显示 todo 对象的 text 属性。

-->
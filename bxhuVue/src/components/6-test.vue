<!--
这里展示了最简单的组件，它接收一个 prop 并渲染出来。
在指南页面了解更多关于组件的内容！
-->

<script setup>
import { ref } from 'vue'
import TodoItem from './6-TodoItem.vue'

const groceryList = ref([
  { id: 0, text: 'Vegetables' },
  { id: 1, text: 'Cheese' },
  { id: 2, text: 'Whatever else humans are supposed to eat' }
])
// ref 和 groceryList: 使用 ref 创建一个响应式变量 groceryList，其中包含一些待办事项，每个待办事项都有 id 和 text 属性

</script>

<template>
  <ol>
    <!--
      我们给每个 todo 项提供它所表示的 todo 对象，
      以便能够动态展示内容。
      同时还需要给每个组件提供一个“key”，
      这在指南的 v-for 部分有详细解释。
    -->
    <TodoItem
      v-for="item in groceryList"
      :todo="item"
      :key="item.id"
    ></TodoItem>
  </ol>
  
<!--  
<ol> 和 <TodoItem>: 在模板部分，使用 <ol> 列表，并通过 v-for 指令遍历 groceryList 数组，为每个待办项创建一个 TodoItem 组件实例。

:todo="item" 和 :key="item.id": 使用 : 绑定将 item 作为 todo 属性传递给 TodoItem 组件，并为每个组件实例设置唯一的 key 属性，确保 Vue 能够高效地更新列表  -->
  
</template>
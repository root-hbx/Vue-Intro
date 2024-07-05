<!--
现在我们将元素的 attribute / property 响应式地绑定到状态上。
这个 :title 语法是 v-bind:title 的简写。
-->

<script setup>
import { ref } from 'vue'

const message = ref('Hello World!')
const isRedNameIsNotKey = ref(true)
// const isRed = ref('red')
const color = ref('green')

function toggleRed() {
  isRedNameIsNotKey.value = !isRedNameIsNotKey.value
}

function toggleColor() {
// color.value = color.value === 'green' ? 'blue' : 'green'
  if (color.value === 'green') {
    color.value = 'yellow';
  } else {
    color.value = 'green';
  }
}
  
</script>

<template>
  <p>
    <span :title="message">
      Text1: Hover your mouse over me for a few seconds to see my dynamically bound title!
    </span>
  </p>

  <!--
  除了普通字符串之外，
  class 绑定还特别支持了对象和数组
  -->
  <p :class="{ red: isRedNameIsNotKey }" @click="toggleRed">
    Text2: This should be red... but click me to toggle it.
  </p>

  <!-- 样式绑定也支持对象和数组 -->
  <p :style="{ color }" @click="toggleColor">
    Text3: This should be green, and should toggle between green and yellow on click.
  </p>
</template>

<style>
.red {
  color: red;
}
</style>
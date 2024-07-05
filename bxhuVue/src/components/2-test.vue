<!--
这个示例展示了如何通过 v-on 指令处理用户输入
-->

<script setup>
import { ref } from 'vue'

const message = ref('Hello World')

function reverseMessage() {
  // 通过其 .value 属性
  // 访问/修改一个 ref 的值。
  message.value = message.value.split('').reverse().join('')
  /*
  .split('')：将字符串拆分成一个字符数组
  	
    如果 message.value 是'hello'，那么 message.value.split('')		
    将返回 ['h', 'e', 'l', 'l', 'o']
	
    .reverse()：反转数组中的字符顺序
  	例如，['h', 'e', 'l', 'l', 'o'] 变成 ['o', 'l', 'l', 'e','h']
	
    .join('')：将反转后的字符数组重新组合成一个字符串
  	例如，['o', 'l', 'l', 'e', 'h'] 变成 'olleh'
  */
}

function fbiWarning() {
  alert('navigation was prevented by admin-bxhu.')
}
</script>

<template>
  <!--
    注意我们不需要在模板中写 .value
    因为在模板中 ref 会自动“解包”
  -->
  <h1>{{ message }}</h1>

  <!--
    绑定到一个方法/函数
    这个 @click 语法是 v-on:click 的简写
  -->

  <!-- 这个按钮绑定了一个点击事件，当按钮被点击时，将调用 reverseMessage 方法-->
  <button @click="reverseMessage">Reverse Message</button>
    <!-- @click 是 v-on:click 的简写形式，用于监听点击事件-->
    <!-- 当用户点击按钮时，Vue 会执行 reverseMessage 方法-->
    <!-- 在网页展示时，显示按钮的名字是"Reverse Message"-->

  <!-- 也可以写成一个内联表达式语句 -->
  <!-- 当按钮被点击时，将在 message 的当前值后面追加一个感叹号 '!' -->
  <button @click="message += '!'">Append "!"</button>
  <!-- 通过 @click="message += '!'" 语法，可以直接在模板中编写简单的 JavaScript 表达式-->
  <!-- 当用户点击按钮时，message 的值会被更新，在其现有内容后追加一个感叹号-->

  <!--
    Vue 也为一些像 e.preventDefault() 和 e.stopPropagation()
    这样的常见任务提供了修饰符。
  -->
  <a href="https://vuejs.org" @click.prevent="fbiWarning">
    A link with e.preventDefault()
  </a>
</template>

<style>
button, a {
  display: block;
  margin-bottom: 5em;
}
</style>
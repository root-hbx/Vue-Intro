<!--
https://eugenkiss.github.io/7guis/tasks/#temp
-->

<script setup>
import { ref } from 'vue'

const c = ref(0)
const f = ref(32)

function setC(e, v = +e.target.value) {
  // 用来更新摄氏度的值。e是事件对象，v是新的摄氏度值（通过从事件对象e中获取）
  c.value = v
  f.value = v * (9 / 5) + 32
}
// 当用户在摄氏度输入框中输入一个新值时，setC函数被调用，更新摄氏度值，并根据公式计算出相应的华氏度值

/*
e.target 是触发事件的目标元素（在这种情况下是输入框）
e.target.value 是目标元素的值，即输入框中的内容
+e.target.value 是一种将字符串转换为数字的快捷方式。JavaScript 中的 + 操作符可用于将一个字符串转换为数字。例如，+'123' 将会返回数字 123
*/
  
  

function setF(e, v = +e.target.value) {
  // 用来更新华氏度的值。e是事件对象，v是新的华氏度值（通过从事件对象e中获取）
  f.value = v
  c.value = (v - 32) * (5 / 9)
}
// 当用户在华氏度输入框中输入一个新值时，setF函数被调用，更新华氏度值，并根据公式计算出相应的摄氏度值  

</script>

<template>
  <input type="number" :value="c" @change="setC"> Celsius 		&nbsp = &nbsp
  <input type="number" :value="f" @change="setF"> Fahrenheit
  
<!--  
<input type="number" :value="c" @change="setC">：
	这是一个数字输入框，显示和输入摄氏度的值。value绑定了响应式数据c，当输入值改变时，触发setC函数
<input type="number" :value="f" @change="setF">：
	这是另一个数字输入框，显示和输入华氏度的值。value绑定了响应式数据f，当输入值改变时，触发setF函数  
-->
  
</template>
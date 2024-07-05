<!--
https://eugenkiss.github.io/7guis/tasks/#flight
-->

<script setup>
import { ref, computed } from 'vue'

const flightType = ref('one-way flight')
const departureDate = ref(dateToString(new Date()))
const returnDate = ref(departureDate.value)

const isReturn = computed(
  () => 
  	flightType.value === 'return flight'
)

/*
计算属性 compute(...)：
	if flightType.value === 'return flight'
  	return True
  else 
  	return False
    
箭头函数 () => { ... } 
	是JavaScript中的一种简洁的函数定义方式。它表示一个匿名函数(LAMBDA)，在这里用作computed的参数，用于计算属性的值
*/

const canBook = computed(
  () =>
    !isReturn.value ||
    stringToDate(returnDate.value) > stringToDate(departureDate.value)
)

function book() {
  alert(
    isReturn.value
      ? `You have booked a return flight leaving on ${departureDate.value} and returning on ${returnDate.value}.`
      : `You have booked a one-way flight leaving on ${departureDate.value}.`
  )
  // alert() 是 JavaScript 中的一个全局函数，用于在浏览器中显示一个简单的警告框(弹窗)，其中包含一条消息
}

function stringToDate(str) {
  const [y, m, d] = str.split('-')
  return new Date(+y, m - 1, +d)
}
/*
	- +y 和 +d 是将字符串转换为数值的简洁方法;
	- m - 1 是将月份调整为 JavaScript Date 对象所需的格式（从 0 开始的月份）
*/

function dateToString(date) {
  return (
    date.getFullYear() +
    '-' +
    pad(date.getMonth() + 1) +
    '-' +
    pad(date.getDate())
  )
}
  
/*
date.getMonth() 是 JavaScript Date 对象的方法，用于获取日期的月份部分。

返回值是从 0 开始的，即 0 表示一月，1 表示二月，依此类推，直到 11 表示十二
*/
  
/*
pad(date.getDate()) 确保日期部分是两位数的字符串表示，例如将 5 转换为 "05"
*/

function pad(n, s = String(n)) {
  return s.length < 2 ? `0${s}` : s
}
// pad(n, s = String(n)) 函数确保一个数字转换为两位数的字符串。如果数字小于 10，则在前面添加 '0'。例如，pad(7) 返回 "07"，而 pad(12) 返回 "12"

</script>


<template>
  <select v-model="flightType">
    <option value="one-way flight">One-way Flight</option>
    <option value="return flight">Return Flight</option>
  </select>

  <input type="date" v-model="departureDate">
  <input type="date" v-model="returnDate" :disabled="!isReturn">
  
<!--  
<input type="date"> 输入框在界面上显示为日期选择器，但在 JavaScript 中，它的值始终是一个字符串，格式为 "YYYY-MM-DD"。

当用户在输入框中选择一个日期时，Vue.js 会自动将该日期转换为这个格式的字符串，并更新绑定的变量  
-->

  <button :disabled="!canBook" @click="book">Book</button>

<!-- 按钮禁用状态 (:disabled="!canBook")：

1. 当 canBook 的值为 true 时，按钮是可用的，用户可以点击它来执行预订操作。
2. 当 canBook 的值为 false 时，按钮被禁用 (and it's grey)，用户无法点击它来执行预订操作。

这通常是基于一些条件逻辑，比如选择航班类型和日期的有效性检查 -->
  
  <p>{{ canBook ? '' : 'Return date must be after departure date.' }}</p>
  
</template>

<style>
select,
input,
button {
  display: block;
  margin: 0.5em 0;
  font-size: 15px;
}

input[disabled] {
  color: #999; 
  /*<input> 元素因为设置了 disabled 属性，所以文本颜色显示为灰色 (#999)*/
}

p {
  color: red; /* the alert-font color */
}
</style>
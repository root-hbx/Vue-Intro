<!--
我们可以使用 v-model 指令在状态和表单输入之间创建双向绑定。
-->

<script setup>
import { ref } from 'vue'

const text = ref('Edit me')
const checked = ref(true)
const checkedNames = ref(['Jack'])
const picked = ref('One')
const selected = ref('A')
const multiSelected = ref(['A'])
</script>

<template>
  <h2>Text Input</h2>
  <input v-model="text">
  <p>{{ text }}</p>
  
	<!--  - 创建了一个文本输入框和一个显示当前输入文本的段落
			- v-model="text" 将输入框的值绑定到 text 变量  -->
	<!-- 在 HTML 标准中，<input> 元素的 type 属性有多种可能的值，

	例如：
	text：文本输入框
	password：密码输入框
	email：电子邮件输入框
	number：数字输入框
	checkbox：复选框
	radio：单选按钮
	...

	如果未指定 type 属性，浏览器会将其默认为 text，即文本输入框。因此，尽管代码中没有显式说明 <input> 是文本输入框，但它的默认行为是如此 -->
  
	<!-- 默认行为，type="text" -->
	<!-- <input v-model="text"> -->

	<!-- 显式指定 type="text" -->
	<!-- <input type="text" v-model="text"> -->

  
  <h2>Checkbox</h2>
  
  <input type="checkbox" id="checkbox" v-model="checked">
  <label for="checkbox">Checked: {{ checked }}</label>

	<!--  创建了一个复选框和一个显示复选框当前选中状态的标签。
		v-model="checked" 将复选框的选中状态绑定到 checked 变量  -->
  
	<!--  id 属性用于唯一标识文档中的一个元素  -->
	<!--  代码示例中，id="checkbox" 的用途主要是将 <label> 元素与对应的 <input> 复选框关联起来。这样，当用户点击 <label> 时，浏览器会自动触发与该标签关联的 <input> 元素的点击事件。  -->
  
	<!-- for="checkbox": 这个属性将标签与 id 为 checkbox 的复选框关联起来。
	点击标签"Checked: true/false"就相当于点击复选框[✅][X]-->
  
  <!--
    多个复选框可以绑定到
    相同的 v-model 数组
  -->
  <h2>Multi Checkbox</h2>
  
  <input type="checkbox" id="jack" value="Jack" v-model="checkedNames">
  <label for="jack">Jack</label>
  
	<!--  复选框的 id 是 jack
	标签的 for 属性是 jack，表示这个标签与 id 为 jack 的复选框关联起来。
	当用户点击标签 Jack 时，浏览器会自动将焦点移到 id="jack" 的复选框上，或者切换其选中状态  -->
  
  <input type="checkbox" id="john" value="John" v-model="checkedNames">
  <label for="john">John</label>
  
  <input type="checkbox" id="mike" value="Mike" v-model="checkedNames">
  <label for="mike">Mike</label>
  
	<!--  value 属性定义了复选框的值。
				- 当复选框被选中时，其 value 会被添加到绑定的数组中；
				- 当复选框未被选中时，其 value 会从数组中移除  -->
  
	<!--  复选框的 value 属性分别为 Jack、John 和 Mike
	v-model="checkedNames" 表示这些复选框的选中状态会与 checkedNames 数组双向绑定。
	当复选框被选中时，value 属性的值（如 Jack、John、Mike）会被添加到 checkedNames 数组中。
	当复选框未被选中时，value 属性的值会从 checkedNames 数组中移除  -->
  
  <p>Checked names: {{ checkedNames }}</p>

  
  <h2>Radio</h2>
  
  <input type="radio" id="one" value="One" v-model="picked">
  <label for="one">One</label>
  
  <br>
  
  <input type="radio" id="two" value="Two" v-model="picked">
  <label for="two">Two</label>
  
  <p>Picked: {{ picked }}</p>

  <h2>Select</h2>
  <select v-model="selected">
  <!-- <select v-model="selected" style="width: 100px;"> 可以设定选项框的宽度 --> 
    <option disabled value="">Please select one :)</option>
    <option>A</option>
    <option>B</option>
    <option>C</option>
  </select>
  <p>Selected: {{ selected }}</p>

  <h2>Multi Select</h2>
  <select v-model="multiSelected" multiple style="width:100px">
    <option>A</option>
    <option>B</option>
    <option>C</option>
  </select>
  <p>Selected: {{ multiSelected }}</p>
</template>
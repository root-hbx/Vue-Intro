<!--
https://eugenkiss.github.io/7guis/tasks/#timer
-->

<script setup>
import { ref, onUnmounted, computed } from 'vue'

const duration = ref(15 * 1000) // 计时器持续时间，初始值为 15 秒（以毫秒计）
const elapsed = ref(0) // 已经过的时间，初始值为 0

let lastTime // 上次更新时间戳
let handle // 动画帧句柄

// 更新计时器状态的函数
const update = () => {
  // 计算已经过的时间
  elapsed.value = performance.now() - lastTime 
  
  // 如果已经过的时间超过了设定的持续时间，取消动画帧请求
  if (elapsed.value >= duration.value) {
    cancelAnimationFrame(handle) 
  } 
  else { // 否则继续请求下一帧动画，并更新计时器状态
    handle = requestAnimationFrame(update) 
  }
}


const reset = () => {
  elapsed.value = 0
  lastTime = performance.now()
  update()
}

const progressRate = computed(
  () =>
		Math.min(elapsed.value / duration.value, 1)
  // 计算已经过的时间与设定的持续时间的比率，并确保比率不超过 1
)

reset() // 每次页面加载时，用于初始化和启动计时器

onUnmounted(
  () => {
  	cancelAnimationFrame(handle)
	}
)
/*
onUnmounted 是 Vue 3 Composition API 提供的一个生命周期钩子函数，用于在组件即将卸载时执行清理操作。

在这里，使用 onUnmounted 监听组件的卸载事件。

当组件即将被卸载时（例如用户离开了当前页面或组件被销毁），会执行传入的回调函数。

在回调函数中，调用 cancelAnimationFrame(handle) 取消当前动画帧的请求，确保在组件卸载时停止计时器的更新，释放资源，避免内存泄漏或不必要的计算

感觉有点像是OOP的析构函数
*/

</script>

<template>
  <label
    >Elapsed Time: <progress :value="progressRate"></progress
  ></label>

<!--  
<progress> 元素显示了一个进度条，它的值由 progressRate 控制，表示当前计时器的进度比率
-->

  <div>{{ (elapsed / 1000).toFixed(1) }}s</div>

  <div>
    Duration: <input type="range" v-model="duration" min="1" max="30000">
    {{ (duration / 1000).toFixed(1) }}s
  </div>
<!--   
<input type="range"> 元素和 Vue 的双向绑定，用户可以直观地通过滑动调节器来选择一个合适的持续时间，同时实时更新显示的文本信息 
 
toFixed(1): 输出数字保留一位小数
-->

  <button @click="reset">Reset</button>
</template>

<style>
.elapsed-container {
  width: 300px;
}

.elapsed-bar {
  background-color: red;
  height: 10px;
}
</style>
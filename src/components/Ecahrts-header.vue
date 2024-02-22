<template>
  <div>
    <header>
      <h1>数据可视化—Echarts <span>（基于vue3实现）</span></h1>
      <div class="showTime">当前时间：{{ formattedTime }}</div>
  </header>
  </div>
</template>

<script lang='ts' setup>
import { ref, onMounted, onUnmounted } from 'vue';

// 初始化定时器
let t:any = null;

// 创建一个响应式变量来存储当前时间
const formattedTime = ref('');

// 更新时间的函数
function updateTime() {
  const dt = new Date();
  const y = dt.getFullYear();
  const mt = dt.getMonth() + 1;
  const day = dt.getDate();
  const h = dt.getHours() < 10 ? '0' + dt.getHours() : dt.getHours();
  const m = dt.getMinutes() < 10 ? '0' + dt.getMinutes() : dt.getMinutes();
  const s = dt.getSeconds();

  formattedTime.value = `${y}年${mt}月${day}日 - ${h}:${m}:${s}`;
}

// 在组件加载时启动定时器
onMounted(() => {
  updateTime();
  t = setInterval(updateTime, 1000);
});

// 在组件卸载时清除定时器
onUnmounted(() => {
  clearInterval(t);
});
</script>

<style scoped>

span{
  font-size: 0.3rem
}
</style>
<template>
  <div>
    <EcahrtsHeader></EcahrtsHeader>
  </div>
  <section class="mainbox">
    <!-- 左 -->
    <div class="column">
      <panelBar></panelBar>
      <panelLine></panelLine>
      <panelPie></panelPie>
    </div>
    <!-- 中 -->
    <div class="column">
<EchartsMap></EchartsMap>
    </div>
    <!-- 右 -->
    <div class="column">
      <panelBar2></panelBar2>
      <panelLine2></panelLine2>
      <panelPie2></panelPie2>
    </div>
  </section>
</template>

<script lang='ts' setup>
import EcahrtsHeader from './components/Ecahrts-header.vue';
import panelBar from './components/panel-bar.vue';
import panelBar2 from './components/panel-bar 2.vue';
import EchartsMap from './components/Echarts-Map.vue';
import panelLine from './components/panel-line.vue';
import panelLine2 from './components/panel-line 2.vue';
import panelPie from './components/panel-pie.vue';
import panelPie2 from './components/panel-pie 2.vue';
</script>

<style scoped>


</style>
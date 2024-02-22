<template>
<div class="panel pie">
              <h2>饼形图-年龄分布</h2>
              <div ref="target" class="chart"></div>
              <div class="panel-footer"></div>
          </div>
</template>

<script lang='ts' setup>
  import {ref,onMounted} from 'vue'
  import * as echarts from 'echarts'
  
  // 初始化实例对象
  const target = ref(null)
  let myChart:any = null

  onMounted(()=>{
    myChart = echarts.init(target.value)
    renderChart()
  })

    
  const renderChart = () =>{
    const option = {
        color: ['#006cff', '#60cda0', '#ed8884', '#ff9f7f', '#0096ff', '#9fe6b8', '#32c5e9', '#1d9dff'],
        tooltip: {
            trigger: 'item',
            formatter: '{a} <br/>{b} : {c} ({d}%)'
        },
        legend: {
            bottom: 0,
            itemHeight: 8,
            itemWidth: 8,
            textStyle: {
                color: '#fff',
                fontSize: 8
            }
        },
        series: [
            {
                name: 'Area Mode',
                type: 'pie',
                radius: [10, 60],
                roseType: 'radius',
                itemStyle: {
                    borderRadius: 2
                },
                label: {
                    fontSize: 10,
                    color: '#fff',
                },
                labelLine: {
                    length: 2,
                    length2: 8

                },
                data: [
                    { value: 20, name: '云南' },
                    { value: 26, name: '北京' },
                    { value: 24, name: '山东' },
                    { value: 25, name: '河北' },
                    { value: 20, name: '江苏' },
                    { value: 25, name: '浙江' },
                    { value: 30, name: '四川' },
                    { value: 42, name: '湖北' }
                ]
            }
        ]
    };
    myChart.setOption(option)
  }

</script>

<style scoped>

</style>
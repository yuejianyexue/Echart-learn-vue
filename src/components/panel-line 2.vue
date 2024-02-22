<template>
  <div class="panel line2">
              <h2>折线图-播放量</h2>
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
    tooltip: {
    trigger: 'axis',
},
legend: {
    top: "0",
    textStyle: {
        color: "rgba(255,255,255,.5)",
        fontSize: "12"
    }
},
grid: {
    top: '30',
    left: '10',
    right: '10',
    bottom: '10',
    containLabel: true
},
xAxis: [
    {
        type: 'category',
        boundaryGap: false,
        data: ["01", "02", "03", "04", "05", "06", "07", "08", "09", "10", "11", "12", "13", "14", "15", "16", "17", "18", "19", "20", "21", "22", "23", "24", "25", "26", "26", "28", "29", "30"],
        axisLabel: {
            textStyle: {
                color: "rgba(255,255,255,.6",
                fontSize: 12
            }
        },
        axisLine: {
            lineStyle: {
                color: "rgba(255,255,255,.2)"
            }
        },
    }
],
yAxis: [
    {
        type: 'value',
        axisTick: { show: false },
        axisLine: {
            lineStyle: {
                color: "rgba(255,255,255,.1)"
            }
        },
        axisLabel: {
            textStyle: {
                color: "rgba(255,255,255,.6)",
                fontSize: 12
            }
        },
        // 修改分割线的颜色
        splitLine: {
            lineStyle: {
                color: "rgba(255,255,255,.1)"
            }
        }
    }
],
series: [
    {
        name: 'Email',
        type: 'line',
        areaStyle: {
            color: {
                x: 0,
                y: 0,
                x2: 0,
                y2: 1,
                colorStops: [{
                    offset: 0, color: 'rgba(1, 132, 213, 1)' // 0% 处的颜色
                }, {
                    offset: 1, color: 'rgba(1, 132, 213, .1)' // 100% 处的颜色
                }],
                global: false, // 缺省为 false
                shadowColor: "rgba(0, 0, 0, 0.1)",
            },

        },
        symbol: "circle",
        symbolSize: 5,
        itemStyle: {
            color: "#0184d5",
            borderColor: "rgba(221, 220, 107, .1)",
            borderWidth: 12
        },
        showSymbol: false,

        smooth: true,
        lineStyle: {
            color: "#0184d5",
            width: 2

        },
        data: [30, 40, 30, 40, 30, 40, 30, 60, 20, 40, 30, 40, 30, 40, 30, 40, 30, 60, 20, 40, 30, 40, 30, 40, 30, 40, 20, 60, 50, 40],
    },
    {
        symbolSize: 5,
        showSymbol: false,

        name: '转发量',
        type: 'line',
        smooth: true,
     
        areaStyle: {
            color: {
                x: 0,
                y: 0,
                x2: 0,
                y2: 1,
                colorStops: [{
                    offset: 0, color: 'rgba(0, 216, 135, 0.9)' // 0% 处的颜色
                }, {
                    offset: 1, color: 'rgba(1, 132, 213, .1)' // 100% 处的颜色
                }],
                global: false, // 缺省为 false
                shadowColor: "rgba(0, 0, 0, 0.1)",
            },
        },
        symbol: "circle",
        itemStyle: {
            color: "#00d887",
            borderColor: "rgba(221, 220, 107, .1)",
            borderWidth: 12
        },
        lineStyle: {
            color: "#00d887",
            width: 2

        }
        ,data: [130, 10, 20, 40, 30, 40, 80, 60, 20, 40, 90, 40, 20, 140, 30, 40, 130, 20, 20, 40, 80, 70, 30, 40, 30, 120, 20, 99, 50, 20],
    }
]

       };
    myChart.setOption(option)
  }

</script>

<style scoped>

</style>
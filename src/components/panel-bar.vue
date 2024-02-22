<template>
  <div class="panel bar">
              <h2>柱形图-就业行业</h2>
              <div ref="target" class="chart"></div>
              <div  class="panel-footer"></div>
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

// 构建option对象

const renderChart = () =>{
  const option = {
        color: ["#2f89cf"],
        tooltip: {
            trigger: "axis",
            axisPointer: {
                // 坐标轴指示器，坐标轴触发有效
                type: "shadow" // 默认为直线，可选为：'line' | 'shadow'
            }
        },
        grid: {
            left: "0%",
            top: "10px",
            right: "0%",
            bottom: "4%",
            containLabel: true
        },
        xAxis: {
            type: 'category',
            data: [
                "旅游行业",
                "教育培训",
                "游戏行业",
                "医疗行业",
                "电商行业",
                "社交行业",
                "金融行业"
            ],
            axisTick: {
                alignWithLabel: true
            },
            // 修改刻度标签 相关样式
            axisLabel: {
                color: "rgba(255,255,255,.6) ",
                fontSize: 8
            },
            // 不显示x坐标轴的样式
            axisLine: {
                show: false
            }
        },
        yAxis: {
            type: 'value',
            axisLabel: {
                color: "rgba(255,255,255,.6) ",
                fontSize: 12,
            },
            //y轴的线条改为2px
            axisLine: {
                lineStyle: {
                    color: "rgba(255,255,255,.1)",
                    width: 2
                }
            },
            // y轴分割线的颜色
            splitLine: {
                lineStyle: {
                    color: "rgba(255,255,255,.1)"
                }
            }
        },
        series: [
            {
                name: "直接访问",
                type: "bar",
                //修改柱子宽度
                barWidth: "35%",
                data: [200, 300, 300, 900, 1500, 1200, 600],
                itemStyle: {
                    // 修改柱子圆角
                    barBorderRadius: 5
                }
            }
        ]
    };
  myChart.setOption(option)
}
    
    //   把配置项目给示例对象
    // 4. 让图表跟随屏幕自动的去适应
    // window.addEventListener("resize", function () {
    //     myChart.resize();
    // });



</script>

<style scoped>

</style>
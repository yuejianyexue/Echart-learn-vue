<template>
    <div class="panel bar">
        <h2>柱形图-供求比例</h2>
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
  var myColor = ["#1089E7", "#F57474", "#56D0E3", "#F8B448", "#8B78F6"]
  
  onMounted(()=>{
    myChart = echarts.init(target.value)
    renderChart()
  })
  
  // 构建option对象
  
  const renderChart = () =>{
    const option = {
        grid: {
            top: "10%",
            left: '22%',
            bottom: '10%',
            //   containLabel: true
        },
        // 不显示x轴
        xAxis: {
            show: false
        },
        yAxis: [{
            type: 'category',
            inverse: true,
            data: ["HTML5", "CSS3", "javascript", "VUE", "NODE"],
            //   不显示y轴线和刻度
            axisLine: {
                show: false
            },
            axisTick: {
                show: false
            },
            axisLabel: {
                color: '#fff'
            },
        },
        {
            show: true,
            inverse: true,
            // y轴右标签
            data: [702, 350, 610, 793, 664],
            // 不显示y轴的线
            axisLine: {
                show: false
            },
            // 不显示刻度
            axisTick: {
                show: false
            },
            axisLabel: {
                textStyle: {
                    fontSize: 12,
                    color: "#fff"
                }
            }
        }
        ],
        series: [
            {
                name: '条',
                type: 'bar',
                data: [70, 34, 60, 78, 69],
                yAxisIndex: 0,
                // 修改第一条柱子的圆角
                itemStyle: {
                    barBorderRadius: 20,
                    color: function (params:any) {
                        return myColor[params.dataIndex]
                    }
                },
                // 柱子之间的距离
                barCategoryGap: 50,
                //柱子的宽度
                barWidth: 10,
                // 显示柱子内的文字
                label: {
                    show: true,
                    position: 'inside',
                    formatter: '{c}%'
                }
            },
            {
                name: '框',
                type: "bar",
                barCategoryGap: 50,
                barWidth: 15,
                itemStyle: {
                    color: "none",
                    borderColor: "#00c1de",
                    borderWidth: 3,
                    barBorderRadius: 15
                },
                data: [100, 100, 100, 100, 100],
                yAxisIndex: 1,
            }
        ]
    };
    myChart.setOption(option)
  }
      
  
  
  </script>
  
  <style scoped>
  
  </style>
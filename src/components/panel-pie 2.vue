<template>
  <div class="panel pie2">
              <h2>饼形图-地区分布</h2>
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
    const option ={
        color: [
            "#065aab",
            "#066eab",
            "#0682ab",
            "#0696ab",
            "#06a0ab",
        ],
        tooltip: {},
        legend: {
            //距离底部为0%
            bottom: "0%",
            // 小图标的宽度和高度
            itemWidth: 8,
            itemHeight: 8,
            // data: ['直接访问', '邮件营销', '联盟广告', '视频广告', '搜索引擎'],
            // 修改图例组件的文字为 12px
            textStyle: {
                color: "rgba(255,255,255,.5)",
                fontSize: 10
            }
        },
        series: [
            {
                name: '年龄分布',
                type: 'pie',
                radius: ['40%', '60%'],
                avoidLabelOverlap: false,
                // itemStyle: {
                //     borderRadius: 10,
                //     borderColor: '#fff',
                //     borderWidth: 2
                // },
                label: {
                    show: false,
                },

                labelLine: {
                    show: false
                },
                data: [
                    { value: 1, name: "0岁以下" },
                    { value: 4, name: "20-29岁" },
                    { value: 2, name: "30-39岁" },
                    { value: 2, name: "40-49岁" },
                    { value: 1, name: "50岁以上" }
                ],
            }
        ]
    };
    myChart.setOption(option)
  }

</script>

<style scoped>

</style>
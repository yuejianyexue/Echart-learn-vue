<template>
 <div class="panel line">
              <h2>折线图-人员变化
                  <a href="javascript:;">2020</a>
                  <a href="javascript:;">2021</a>
              </h2>
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

  var yearData = [
        {
            year: "2020", // 年份
            data: [
                // 两个数组是因为有两条线
                [24, 40, 101, 134, 90, 230, 210, 230, 120, 230, 210, 120],
                [40, 64, 191, 324, 290, 330, 310, 213, 180, 200, 180, 79]
            ]
        },
        {
            year: "2021", // 年份
            data: [
                // 两个数组是因为有两条线
                [123, 175, 112, 197, 121, 67, 98, 21, 43, 64, 76, 38],
                [143, 131, 165, 123, 178, 21, 82, 64, 43, 60, 19, 34]
            ]
        }
    ];
    
  const renderChart = () =>{
    const option = {

color: ['#00f2f1', '#ed3f35'],
tooltip: {
    trigger: 'axis'
},
legend: {
    textStyle: {
        color: '#4c9bfd' // 图例文字颜色
    },
    right: '10%' // 距离右边10%

},
grid: {
    top: '20%',
    left: '3%',
    right: '4%',
    bottom: '3%',
    show: true,
    borderColor: '#012f4a',
    containLabel: true
},
xAxis: {
    type: 'category',
    axisTick: {
        show: false // 去除刻度线
    },
    axisLabel: {
        color: '#4c9bfd' // 文本颜色
    },
    axisLine: {
        show: false // 去除轴线
    },
    boundaryGap: false,  // 去除轴内间距
    data: ['1月', '2月', '3月', '4月', '5月', '6月', '7月', '8月', '9月', '10月', '11月', '12月'],
},
yAxis: {
    type: 'value',
    axisTick: {
        show: false  // 去除刻度
    },
    axisLabel: {
        color: '#4c9bfd' // 文字颜色
    },
    splitLine: {
        lineStyle: {
            color: '#012f4a' // 分割线颜色
        },
        boundaryGap: false  // 去除轴内间距

    }
},
series: [{
    name: '新增粉丝',
    data: yearData[0].data[0],
    type: 'line',
    // 折线修饰为圆滑
    smooth: true
}, {
    name: '新增游客',
    data: yearData[0].data[1],

    type: 'line',
    smooth: true
}
]

       };
    //    $('.line h2 ').on('click', 'a', function () {
    //     var obj = yearData[$(this).index()];
    //     option.series[0].data = obj.data[0];
    //     option.series[1].data = obj.data[1];
    //     // 重新渲染
    //     myChart.setOption(option);
    // })
    myChart.setOption(option)
  }


</script>

<style scoped>

</style>
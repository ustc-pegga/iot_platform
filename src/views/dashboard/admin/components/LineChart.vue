<template>
  <div :class="className" :style="{height:height,width:width}" />
</template>

<script>
import echarts from 'echarts'
require('echarts/theme/macarons') // echarts theme
import resize from './mixins/resize'

export default {
  mixins: [resize],
  props: {
    className: {
      type: String,
      default: 'chart'
    },
    width: {
      type: String,
      default: '100%'
    },
    height: {
      type: String,
      default: '350px'
    },
    autoResize: {
      type: Boolean,
      default: true
    },
    chartData: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      chart: null,
      color_list: ['#FF005A', '#3888fa', '#66e0e3', '#ffc300', '#8663e1', '#00bfaa', '#ff6f00', '#7e57c2', '#5c6bc0', '#42a5f5', '#29b6f6', '#26c6da', '#26a69a', '#66bb6a', '#9ccc65', '#d4e157', '#ffee58', '#ffca28', '#ffa726', '#ff7043', '#8d6e63', '#bdbdbd', '#78909c']
    }
  },
  watch: {
    chartData: {
      deep: true,
      handler(val) {
        this.setOptions(val)
      }
    }
  },
  mounted() {
    this.$nextTick(() => {
      this.initChart()
    })
  },
  beforeDestroy() {
    if (!this.chart) {
      return
    }
    this.chart.dispose()
    this.chart = null
  },
  methods: {
    initChart() {
      this.chart = echarts.init(this.$el, 'macarons')
      this.setOptions(this.chartData)
    },
    setOptions(data) {
      const series = []
      const legend = []
      var xarix = []
      var idx = 0
      console.log(data)
      for (const key in data) {
        const item = data[key]
        legend.push(item.name)
        xarix = item.type
        series.push({
          name: item.name,
          type: 'line',
          data: item.data,
          itemStyle: {
            normal: {
              color: this.color_list[idx],
              lineStyle: {
                color: this.color_list[idx],
                width: 2
              }
            }
          },
          smooth: true,
          animationDuration: 2800,
          animationEasing: 'cubicInOut'
        })
        idx++
      }
      console.log(series)
      console.log(legend)
      console.log(xarix)
      this.chart.clear()
      this.chart.setOption({
        xAxis: {
          name: '时间',
          data: xarix.flat(),
          boundaryGap: false,
          axisTick: {
            show: false
          }
        },
        grid: {
          left: 10,
          right: 10,
          bottom: 20,
          top: 30,
          containLabel: true
        },
        tooltip: {
          trigger: 'axis',
          axisPointer: {
            type: 'cross'
          },
          padding: [5, 10]
        },
        yAxis: {
          name: legend[0],
          axisTick: {
            show: false
          }
        },
        legend: {
          data: legend
        },
        series: series
      })
    }
  }
}
</script>

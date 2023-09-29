<template>
  <div class="dashboard-editor-container">
    <github-corner class="github-corner" />

    <!-- <panel-group @handleSetLineChartData="handleSetLineChartData" /> -->
    <el-row :xs="24" :sm="24" :lg="8">
      <div class="chart-wrapper">
        <date @handleDateSelection="handleDateSelection" />
      </div>
    </el-row>
    <el-row style="background:#fff;padding:16px 16px 0;margin-bottom:32px;">
      <line-chart :chart-data="lineChartData" />
    </el-row>
    <el-row :xs="24" :sm="24" :lg="8">
      <div class="chart-wrapper">
        <choose-chart @handleSwitchChange="handleSwitchChange" />
      </div>
    </el-row>
    <!-- <el-row :gutter="32">
      <el-col :xs="24" :sm="24" :lg="8">
        <div class="chart-wrapper">
          <raddar-chart />
        </div>
      </el-col>
      <el-col :xs="24" :sm="24" :lg="8">
        <div class="chart-wrapper">
          <pie-chart />
        </div>
      </el-col>
      <el-col :xs="24" :sm="24" :lg="8">
        <div class="chart-wrapper">
          <bar-chart />
        </div>
      </el-col>

    </el-row>

    <el-row :gutter="8">
      <el-col :xs="{span: 24}" :sm="{span: 24}" :md="{span: 24}" :lg="{span: 12}" :xl="{span: 12}" style="padding-right:8px;margin-bottom:30px;">
        <transaction-table />
      </el-col>
      <el-col :xs="{span: 24}" :sm="{span: 12}" :md="{span: 12}" :lg="{span: 6}" :xl="{span: 6}" style="margin-bottom:30px;">
        <todo-list />
      </el-col>
      <el-col :xs="{span: 24}" :sm="{span: 12}" :md="{span: 12}" :lg="{span: 6}" :xl="{span: 6}" style="margin-bottom:30px;">
        <box-card />
      </el-col>
    </el-row> -->
  </div>
</template>

<script>
// import GithubCorner from '@/components/GithubCorner'
// import PanelGroup from './components/PanelGroup'
import LineChart from './components/LineChart'
import ChooseChart from './components/ChooseChart'
import Date from './components/Date'
// import { showSettings } from '@/settings'
// import { start } from 'nprogress'
// import RaddarChart from './components/RaddarChart'
// import PieChart from './components/PieChart'
// import BarChart from './components/BarChart'
// import TransactionTable from './components/TransactionTable'
// import TodoList from './components/TodoList'
// import BoxCard from './components/BoxCard'

const lineChartData = {
  '光照': {
    day: {
      name: '光照',
      // expectedData: [100, 120, 161, 134, 105, 160, 165, 123,123],
      data: [45, 72, 14, 89, 33, 56, 91, 7, 25],
      type: ['00:00', '03:00', '06:00', '09:00', '12:00', '15:00', '18:00', '21:00', '24:00']
    },
    week: {
      name: '光照',
      // expectedData: [200, 192, 120, 144, 160, 130, 140],
      data: [32, 78, 11, 95, 45, 67, 88],
      type: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
    },
    month: {
      name: '光照',
      // expectedData: [80, 100, 121, 104, 105, 90, 100, 123, 132, 111, 102, 123, 324, 456],
      data: [47, 82, 13, 64, 29, 95, 50, 78, 21, 37, 69, 94],
      type: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec']
    },
    year: {
      name: '光照',
      // expectedData: [130, 140, 141, 142, 145, 150, 160],
      data: [58, 14, 79, 33, 92, 7, 41],
      type: ['2016', '2017', '2018', '2019', '2020', '2021', '2022']
    }
  },
  '温度': {
    day: {
      name: '温度',
      // expectedData: [100, 120, 161, 134, 105, 160, 165, 123,123],
      data: [68, 12, 76, 23, 98, 41, 15, 50, 88],
      type: ['00:00', '03:00', '06:00', '09:00', '12:00', '15:00', '18:00', '21:00', '24:00']
    },
    week: {
      name: '温度',
      // expectedData: [200, 192, 120, 144, 160, 130, 140],
      data: [15, 89, 42, 63, 50, 27, 71],
      type: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
    },
    month: {
      name: '温度',
      // expectedData: [80, 100, 121, 104, 105, 90, 100, 123, 132, 111, 102, 123, 324, 456],
      data: [18, 56, 79, 42, 8, 35, 67, 23, 91, 14, 73, 61],
      type: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec']
    },
    year: {
      name: '温度',
      // expectedData: [130, 140, 141, 142, 145, 150, 160],
      data: [26, 69, 47, 81, 12, 54, 95],
      type: ['2016', '2017', '2018', '2019', '2020', '2021', '2022']
    }
  },
  '电流': {
    day: {
      name: '电流',
      // expectedData: [100, 120, 161, 134, 105, 160, 165, 123,123],
      data: [18, 94, 37, 62, 51, 29, 83, 5, 42],
      type: ['00:00', '03:00', '06:00', '09:00', '12:00', '15:00', '18:00', '21:00', '24:00']
    },
    week: {
      name: '电流',
      // expectedData: [200, 192, 120, 144, 160, 130, 140],
      data: [55, 8, 76, 29, 94, 37, 19],
      type: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
    },
    month: {
      name: '电流',
      // expectedData: [80, 100, 121, 104, 105, 90, 100, 123, 132, 111, 102, 123, 324, 456],
      data: [30, 88, 5, 47, 62, 11, 74, 40, 97, 53, 86, 26],
      type: ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec']
    },
    year: {
      name: '电流',
      // expectedData: [130, 140, 141, 142, 145, 150, 160],
      data: [63, 18, 72, 5, 37, 88, 25],
      type: ['2016', '2017', '2018', '2019', '2020', '2021', '2022']
    }
  }
}

export default {
  name: 'DashboardAdmin',
  components: {
    // GithubCorner,
    // PanelGroup,
    LineChart,
    ChooseChart,
    Date
    // RaddarChart,
    // PieChart,
    // BarChart,
    // TransactionTable
    // TodoList,
    // BoxCard
  },
  data() {
    return {
      date: 'day',
      lineChartData: lineChartData['光照']['day'],
      switch_list: [
        {
          name: '光照',
          value: true
        },
        {
          name: '温度',
          value: false
        },
        {
          name: '电流',
          value: false
        }
      ]

    }
  },
  methods: {
    // handleSetLineChartData(type) {
    //   this.lineChartData = lineChartData[type]
    // },
    handleDateSelection(type) {
      this.date = type
      // console.log(this.date)
      this.draws()
    },
    handleSwitchChange(switches) {
      this.switch_list = switches
      console.log(this.switch_list)
      this.draws()
    },
    draws() {
      var tmp = {}
      for (const item of this.switch_list) {
        const key = item.name
        const value = item.value
        // console.log(key);
        // console.log(value);
        if (value) {
          tmp[key] = lineChartData[key][this.date]
        }
      }
      // console.log(tmp)
      this.lineChartData = tmp
    }
  }
}
</script>

<style lang="scss" scoped>
.dashboard-editor-container {
  padding: 32px;
  background-color: rgb(240, 242, 245);
  position: relative;

  .github-corner {
    position: absolute;
    top: 0px;
    border: 0;
    right: 0;
  }

  .chart-wrapper {
    background: #fff;
    padding: 16px 16px 0;
    margin-bottom: 32px;
  }
}

@media (max-width:1024px) {
  .chart-wrapper {
    padding: 8px;
  }
}
</style>

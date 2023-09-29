<template>
  <div :class="className">
    <el-radio-group v-model="selectedDate" @change="handleDateSelection">
      <el-radio label="year">年</el-radio>
      <el-radio label="month">月</el-radio>
      <el-radio label="week">周</el-radio>
      <el-radio label="day">日</el-radio>
    </el-radio-group>
  </div>
</template>

<script>
export default {
  props: {
    selectedDate: {
      type: String, // 从父组件传递的选择值
      default: 'day'
    }
  },
  methods: {
    handleDateSelection(selectedItem) {
      this.$emit('handleDateSelection', selectedItem) // 向父组件发出事件，传递选择值
    }
  }
}
</script>

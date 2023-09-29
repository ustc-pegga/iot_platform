<template>
  <div :class="className">
    <el-switch v-for="(item, index) in switches" :key="index" v-model="item.value" @change="handleSwitchChange(item, index)" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      switches: [
        { name: '光照', value: true },
        { name: '温度', value: false },
        { name: '电流', value: false }
      ] // 存储多个开关的值和名称
    }
  },
  methods: {
    handleSwitchChange(item, index) {
      // 当开关值发生变化时，触发自定义事件将值、名称和索引传递给父组件
      this.$emit('handleSwitchChange', this.switches)
    }
  }
}
</script>

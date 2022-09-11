<template>
  <el-result
      icon="error"
      title="禁止访问"
      sub-title="很抱歉，您没有权限访问该内容"
  >
    <template #extra>
      <el-button type="primary" @click="changePage">返回</el-button>
    </template>
  </el-result>
</template>

<script lang="ts" setup>
  const emit = defineEmits(['changePage'])
  const changePage = () => {
    emit('changePage', 1)
  }
</script>

<style scoped>

</style>

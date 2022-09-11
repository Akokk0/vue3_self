<template>
  <el-scrollbar height="400px">
    <p class="scrollbar-demo-item">姓名：{{self.name}}</p>
    <p class="scrollbar-demo-item">班级：{{self.className}}</p>
    <p class="scrollbar-demo-item">学号：{{self.idNumber}}</p>
    <p class="scrollbar-demo-item">爱好：{{self.hobby}}</p>
    <p class="scrollbar-demo-item">联系方式：{{self.tel}}</p>
    <p class="scrollbar-demo-item">电子邮箱：{{self.email}}</p>
  </el-scrollbar>
</template>

<script lang="ts" setup>
  import {reactive} from "vue";

  const self = reactive({
    name: '周昊',
    className: '计科2011',
    idNumber: 20104011117,
    tel: 18508349540,
    email: 'admin@akokko.com',
    hobby: 'Code, Game, Computer Painting, 日本語を勉強します'
  })
</script>

<style scoped>
  .scrollbar-demo-item {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 50px;
    margin: 10px;
    text-align: center;
    border-radius: 4px;
    background: var(--el-color-primary-light-9);
    color: var(--el-color-primary);
  }
</style>

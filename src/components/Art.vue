<template>
  <div v-loading.fullscreen.lock="fullscreenLoading">
    <el-row :gutter="12">
      <el-col :span="8" v-for="item in artList" :key="item">
        <el-card shadow="hover">
          <el-image :src="item"/>
        </el-card>
      </el-col>
    </el-row>
  </div>
</template>

<script lang="ts" setup>
import {ref} from "vue";

  const artList = ref([
      require("@/assets/art/1.jpg"),
      require("@/assets/art/2.jpg"),
      require("@/assets/art/3.jpg"),
      require("@/assets/art/4.png"),
      require("@/assets/art/5.png"),
      require("@/assets/art/6.jpg"),
  ])

  const fullscreenLoading = ref(true)

  let loading = setInterval(() => {
    if (document.readyState === 'complete') {
      fullscreenLoading.value = false
      clearInterval(loading)
    }
  }, 500)
</script>

<style scoped lang="less">

</style>

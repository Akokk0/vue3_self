<template>
  <div>
    <el-row :gutter="12">
      <el-col :span="8" v-for="item in artList" :key="item">
        <el-card shadow="hover" v-loading="imgLoading">
          <el-image :src="item"  @load="imgLoaded"/>
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
      require("@/assets/art/3.jpg")
  ])

  const imgLoading = ref(true)

  for (let index of artList.value) {
    let name = 'imgLoad' + index
    console.log(name)
  }

  const imgLoaded = (e: Event) => {
    imgLoading.value = false
    console.log(e)
  }

  /*const myRef = ref<Document[]>([]);

  const artDomList = (el: Document) => {
    myRef.value.push(el);
  };*/

  /*let loading = setInterval(() => {
    /!*if (document.readyState === 'complete') {
      fullscreenLoading.value = false
      clearInterval(loading)
    }*!/
  }, 500)*/
</script>

<style scoped lang="less">

</style>

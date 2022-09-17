<template>
  <div class="common-layout" v-loading.fullscreen.lock="fullscreenLoading">
    <el-container>
      <el-header>
        <img id="img" src="@/assets/avatar.png">
      </el-header>
      <el-main>
        <!--    走马灯    -->
        <el-carousel :interval="4000" type="card" height="300px">
          <el-carousel-item v-for="item in carousel" :key="item">
            <el-image class="selfImg" fit="fill" :src="item"/>
          </el-carousel-item>
        </el-carousel>
        <!--    卡片     -->
        <el-card class="box-card">
          <template #header>
            <div class="card-header">
              <el-badge :is-dot="personDot" class="item">
                <el-button type="primary" @click="currentPage = 1">个人信息</el-button>
              </el-badge>
              <el-badge value="3" class="item">
                <el-button type="primary" @click="currentPage = 3">喜欢的作品</el-button>
              </el-badge>
              <el-badge :is-dot="privacyDot" class="item">
                <el-button type="danger" @click="currentPage = 2">Privacy</el-button>
              </el-badge>
            </div>
          </template>
          <div>
            <component :is="currentComponent[currentPage]" @changePage="currentPage = 1"></component>
          </div>
        </el-card>
<!--        <el-card class="box-card">
          <template #header>
            <div class="card-header">
              <span>Card name</span>
              <el-button class="button" text>Operation button</el-button>
            </div>
          </template>
          <div v-for="o in 4" :key="o" class="text item">{{ 'List item ' + o }}</div>
        </el-card>-->
<!--        <el-scrollbar height="400px">
          <p class="scrollbar-demo-item">姓名：{{self.name}}</p>
          <p class="scrollbar-demo-item">班级：{{self.className}}</p>
          <p class="scrollbar-demo-item">学号：{{self.idNumber}}</p>
          <p class="scrollbar-demo-item">爱好：{{self.hobby}}</p>
          <p class="scrollbar-demo-item">联系方式：{{self.tel}}</p>
          <p class="scrollbar-demo-item">电子邮箱：{{self.email}}</p>
        </el-scrollbar>-->
      </el-main>
    </el-container>
  </div>
</template>

<script lang="ts" setup>
  import {reactive, ref, watch} from "vue";
  import Self from "@/components/Self.vue"
  import Privacy from "@/components/Privacy.vue"
  import Art from "@/components/Art.vue"

  // 获取dom对象
  /*const personal = ref()
  const draw = ref()
  const priv = ref()*/

  const currentPage = ref(1)

  const currentComponent = reactive({
    1: Self,
    2: Privacy,
    3: Art
  })

  const carousel = [
    require("@/assets/carousel/1.jpg"),
    require("@/assets/carousel/2.jpg"),
    require("@/assets/carousel/3.png"),
    require("@/assets/carousel/4.jpg")
  ]

  // 控制小红点
  const personDot = ref(false)
  const privacyDot = ref(true)

  const fullscreenLoading = ref(true)

  let loading = setInterval(() => {
    if (document.readyState === 'complete') {
      fullscreenLoading.value = false
      clearInterval(loading)
    }
  },500)

  watch(currentPage, (newValue, oldValue) => {
    switch (newValue) {
      case 1:
        personDot.value = false
        privacyDot.value = true
            break
      case 3:
        personDot.value = true
        privacyDot.value = true
            break
      case 2:
        personDot.value = true
        privacyDot.value = false
    }
  })

  /*const toMyWebPage = () => {
    location.href = "http://akokko.com"
  }*/

  /*const changeCurrentPage = (page: number) => {
    currentPage.value = page
  }*/
</script>

<style lang="less" scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  #img {
    padding-top: 9px;
    height: 80px;
    width: 80px;
    border-radius: 15px;
  }
  .common-layout {
    background-color: pink;
    width: 100%;
    height: 100%;
    padding: 1px;
    border-radius: 25px;
  }

  .card-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  .text {
    font-size: 14px;
  }

  .item {
    margin-bottom: 18px;
  }

  .box-card {
    border-radius: 9px;
    width: 99%;
  }

  .selfImg {
    border-radius: 8px;
  }

}
</style>

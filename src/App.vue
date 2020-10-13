<template>
  <div>
    <img alt="Vue logo" src="./assets/logo.png">
    <div>
      <h2>欢迎光临红浪漫洗浴中心</h2>
      <div>随机出现一张狗狗的照片</div>
      <div v-if="res.loading">Loading...</div>
      <img v-if="res.loaded" :src="res.result.message" @click="getDog"/>
    </div>
  </div>
</template>

<script lang="ts">
import { 
  ref, 
  onMounted
} from 'vue';
import useAxios from './hooks/useAxios'
const app = {
  name: 'App',
  setup() {
    const res = ref({})
    const getDog = () => {
      res.value = useAxios('https://dog.ceo/api/breeds/image/random')
    }
    onMounted(() => setInterval(getDog, 3000))
    return {
      res,
      getDog
    }
  }
}
export default app
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

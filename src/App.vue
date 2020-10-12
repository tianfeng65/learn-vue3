<template>
  <div>
    <img alt="Vue logo" src="./assets/logo.png">
    <div>
      <h2>欢迎光临红浪漫洗浴中心</h2>
      <div>请选择一位美女为你服务</div>
    </div>
    <div>
      <button 
        v-for="(item, index) of girls" 
        :key="index"
        @click="selectGirlFun(index)"
      >
        {{index}}:{{item}}
      </button>
    </div>
    <div>你选择了【{{selectedGirl}}】为你服务！</div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';

export default defineComponent({
  name: 'App',
  setup() {
    const girls = ref(['不知火舞', '王昭君', '蔡文姬'])
    const selectedGirl = ref('')
    const selectGirlFun = (index: number) => {
      selectedGirl.value = girls.value[index]
    }
    return {
      girls,
      selectedGirl,
      selectGirlFun
    }
  }
});
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

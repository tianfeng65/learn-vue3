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
import { 
  defineComponent,
  reactive, 
  ref, 
  toRefs,
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onRenderTracked,
  onRenderTriggered
} from 'vue';
interface DataProps {
  girls: string[];
  selectedGirl: string;
  selectGirlFun: (index: number) => void;
}
export default defineComponent({
  name: 'App',
  setup() {
    const data: DataProps = reactive({
      girls: ref(['不知火舞', '王昭君', '蔡文姬']),
      selectedGirl: ref(''),
      selectGirlFun: (index: number) => {
        data.selectedGirl = data.girls[index]
      } 
    })
    onRenderTracked((event) => {
      console.log('状态跟踪钩子函数执行--onRenderTracked()')
      console.log(event)
    })
    onRenderTriggered((event) => {
      console.log('状态触发钩子函数执行--onRenderTriggered()')
      console.log(event)
    })
    const refData = toRefs(data)
    return {
      ...refData
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

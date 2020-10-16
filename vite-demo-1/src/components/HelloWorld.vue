<template>
  <h1>{{ msg }}</h1>
  <button @click="add">count is: {{ state.count }}---{{double}}</button>
  <p>{{num}}---{{a}}---{{b}} ---- {{obj2.a}}</p>
</template>

<script>
import {reactive, computed, ref, onMounted, toRefs} from 'vue'
export default {
  setup(){
    const {state, double} = useCounter(1)
    const num = ref(3) // ref的方法声明变量
    function add() {
      state.count++ // 使用reactive直接更改就行
      num.value++ // 使用.value去更改ref的值，从而更新视图
    }
    // 生命周期都带上了on
    // 销毁的生命周期变成了onBeforeUnmounted 和 onUnmounted
    // 去掉了created和beforeCreated变成了setup
    onMounted(() => {
      console.log('mounted')
    })
    const obj = reactive({
      a: 'xixi',
      b: 'jaja'
    })
    const obj2 = reactive({
      a: 'xixiobj2obj2'
    })
    // toRefs(obj)，相当于obj展开了，每一个属性都单独的声明了一次，单独的去执行了ref,所以页面使用的时候直接a便可访问到
    // obj2是直接返回了，那么页面就需要obj2.a这样去访问的，
    // 总之ref或者toRefs都是直接拿属性去绑定页面，reactive是相当于只剩一个大的info去打点访问属性
    // 就比如有人喜欢把商品详情的所有信息一个个去负值，有人喜欢直接用一个对象，页面打点获取
    return {state, add, double, num, ...toRefs(obj),obj2}
  }
}
// 抽离公共的方法，不需要每次改很多地方，能很好的维护
function useCounter(count, n) {
  const state = reactive({
    count: count
  })
  const double = computed(() => {
    return state.count*2
  })
  return {state, double}
}
</script>

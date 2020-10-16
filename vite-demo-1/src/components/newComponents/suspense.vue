<template>
  <h2>suspense</h2>
  <h5>使用的场景就是：比如列表页面，先出来加载的loading,登机口返回就要展示列表的数据就是异步组件</h5>
  <h5>可以把loading变成公共的组件，每个页面都引入</h5>
  <Suspense>
    <!-- 异步组件 -->
    <template #default>
      <AsyncComponent :timeout="3000"></AsyncComponent>
    </template>
    <!-- 加载中组件 -->
    <template #fallback>
      <Loading></Loading>
    </template>
  </Suspense>
</template>
<script>
import AsyncComponent from './asyncComponent.vue'
import Loading from './loading.vue'
export default {
  components: {
    AsyncComponent,
    Loading
  }
}
</script>

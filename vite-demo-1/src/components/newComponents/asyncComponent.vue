<template>
  <h3>这是一个异步小组件</h3>
</template>
<script>
  // 这里比如掉了后端的列表接口
  function sleep(timeout) {
    return new Promise(resolve => setTimeout(resolve, timeout))
  }
  export default {
    name: 'AsyncComponent',
    props: {
      timeout: {
        type: Number,
        required: true
      }
    },
    async setup(props) {
      await sleep(props.timeout)
    }
  }
  </script>
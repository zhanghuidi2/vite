<template>
  <h2>加载中{{loading}}</h2>
</template>
<script>
import {ref, onUnmounted} from 'vue'
export default {
  setup() {
    let loading = ref('')
    let i = 0
    let arr = ': …… :'
    let timer = setInterval(() => {
      loading.value = arr[i]
      i = (i + 1) % 4
    }, 350);
  }
}
</script>
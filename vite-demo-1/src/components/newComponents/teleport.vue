<template>
  <button @click="isOpen = true">打开</button>
  <Teleport to="#foot-container">
    <div v-if="isOpen">
      <p>这个to是在index.html里的div的id</p>
      <button @click="isOpen = false">取消</button>
    </div>
  </Teleport>
</template>
<script>
import {ref} from 'vue'
export default {
  setup() {
    const isOpen = ref(false)
    return {isOpen}
  }
}
</script>
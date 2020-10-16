<template>
  <HelloWorld msg="Hello Vue 3.0 + Vite" />
  <TelePort></TelePort>
  <Supense></Supense>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import TelePort from './components/newComponents/teleport.vue'
import Supense from './components/newComponents/suspense.vue'
export default {
  name: 'App',
  components: {
    HelloWorld,
    TelePort,
    Supense
  }
}
</script>

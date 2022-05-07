<template>
  <div class="home">
    <HelloWorld msg="message"/>
    <img alt="Vue logo" src="../assets/logo.png">

  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorld
  },
  data(){
  }
}
</script>

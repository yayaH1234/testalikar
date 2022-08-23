<template>
  <div class="home">
    <!--img alt="Vue logo" src="../assets/logo.png"-->
    <!--HelloWorld msg="Welcome to Your Vue.js App"/-->
    <Testindex :idQuestion=0 />
  </div>
</template>

<script>
// @ is an alias to /src
//import HelloWorld from '@/components/HelloWorld.vue'
import Testindex from '@/components/Testindex.vue'
export default {
  name: 'HomeView',
  components: {
    Testindex
  }
}
</script>

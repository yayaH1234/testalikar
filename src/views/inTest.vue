<template>
  <div class="home">
  
    <!--Testindex :idQuestion="this.indexQuestion" /-->
    <Testindex :idQuestion=0 />
  </div>
</template>

<script>
// @ is an alias to /src
//import HelloWorld from '@/components/HelloWorld.vue'
import Testindex from '@/components/Testindex.vue'
export default {
  name: 'inTest',
  components: { 
   Testindex
  },
data(){
     return {
           indexQuestion :  0

     }}, 
      methods: {
         initData(){
     //this.$route.params.id
     this.indexQuestion=parseInt(this.$route.params.id)
     //  this.indexQuestion--
     //  alert(this.indexQuestion)
     }
     
     }
     ,
        created () {
            this.initData()
        }

     



}
</script>

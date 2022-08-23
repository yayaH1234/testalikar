<template>
  <div class="container">
   
    <div class="row">
      
      <div class="mb-3">
       People who think they know everything are a great annoyance to those of us who do.
      </div>
      <div class="mb-3">
         <p> {{ this.$store.state.Score }} / 5</p>
      </div>
      <div class="mb-3">
        <button type="button" class="btn btn-success" @click="onClickBtn">confirme your test</button>
        <br/><br/>
        <button type="button" class="btn btn-light" @click="onClickBtn">Restart Test</button>
      </div>
    </div>

  </div>
</template>

<script>

export default {
  name: 'ResultScore',
          methods: {

onClickBtn(){
  this.$store.state.Score=0
   this.$router.push({name:'home'})
}
  }
  
}
</script>
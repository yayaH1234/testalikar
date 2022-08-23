<template>
  <div class="container">
   
    <div class="row">
      
      <div class="mb-3">
        blablablablablablablablablablablabla
      </div>
      <div class="mb-3">
         <p> {{ this.$store.state.Score }} / 5</p>
      </div>
      <div class="mb-3">
        <button type="button" class="btn btn-success">confirme your test</button>
        <br/><br/>
        <button type="button" class="btn btn-light">Restart Test</button>
      </div>
    </div>

  </div>
</template>

<script>

export default {
  name: 'ResultScore',
  
}
</script>
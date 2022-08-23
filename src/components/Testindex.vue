<template>
  <div class="container">








  <div class="row">
    <div class="col-md-3">

      <div class="row">
      
<div class="container">
        <div class="col">
          <img class="bd-placeholder-img" width="200" height="250" :src="this.imgurl" />

        </div>
</div>
      </div>

    </div>
    <div class="col">
      <div class="row">
      
        <div class="col">
          
           <div class="row">
                                <div class="col mr-auto "><a class="btn btn-primary">{{ this.idQ }} - 5 </a>  </div>
                                <div class="col text-primary">  00:{{ countDown }} </div>
                                
            </div>
            
<hr>
              <br/>
            
            
            <div class="container">
            <div class="row">
                      {{ this.question }}
            </div>
            <br/>



            <div class="row">
                      
                      <ul class="list-group">
             
  <li v-for="answer in answerslists" :key="answer.id" class="list-group-item"   @click="bestanswer(answer)">
    {{ answer.label }}
  </li>
                      </ul>


                      <!--ul class="list-group">
                        <li class="list-group-item active">rep1</li>
                        <li class="list-group-item">rep2</li>
                        <li class="list-group-item">rep3</li>
                        <li class="list-group-item">rep4</li>
                      </ul-->

            </div>
            

 <br/>
                <div class="row">
            <div class="col offset-md-3">  <button type="button" class="btn btn-success" @click="onClickNext" :disabled="this.checkedans === null" >Next</button> </div>
                                
            </div>
           


            </div>
           
            
        </div>
        
      </div>
    </div>
    <!--
     <div class="col-md-6">
      <div class="row g-0 border rounded overflow-hidden flex-md-row mb-4 shadow-sm h-md-250 position-relative">
        <div class="col p-4 d-flex flex-column position-static">
          <strong class="d-inline-block mb-2 text-success">Design</strong>
          <h3 class="mb-0">Post title</h3>
          <div class="mb-1 text-muted">Nov 11</div>
          <p class="mb-auto">This is a wider card with supporting text below as a natural lead-in to additional content.</p>
          <a href="#" class="stretched-link">Continue reading</a>
        </div>
        <div class="col-auto d-none d-lg-block">
          <svg class="bd-placeholder-img" width="200" height="250" xmlns="http://www.w3.org/2000/svg" role="img" aria-label="Placeholder: Thumbnail" preserveAspectRatio="xMidYMid slice" focusable="false"><title>Placeholder</title><rect width="100%" height="100%" fill="#55595c"/><text x="50%" y="50%" fill="#eceeef" dy=".3em">Thumbnail</text></svg>

        </div>
      </div>
    </div>
    -->
  </div>











  </div>
</template>

<script>

export default {
  name: 'HelloWorld',
  props: {
    idQuestion: Number
  },  data() {
            return {
                countDown: 60,
                answerslists : [],
                question : "",
                listD : [],
                idQ : 0,
                imgurl : "",
                checkedans:null
            }
        },
        methods: {
            countDownTimer () {
                if (this.countDown > 0) {
                    setTimeout(() => {
                        this.countDown -= 1
                        this.countDownTimer()
                    }, 1000)
                }
            },
            initData(){
              this.listD=this.$store.state.dataListe[this.idQuestion]
              this.answerslists=this.listD.answers
              this.question=this.listD.label
              this.idQ=this.listD.id
              this.countDown=this.listD.time
              this.imgurl=this.listD.image
            },
            bestanswer(an){
            this.checkedans=an
              


            },
            onClickNext(){
            
              this.idQ++
              alert('/inTest/'+this.idQ)
                 this.$router.push({name:'intest',params: {id:this.idQ}})
              
            /*  if(this.checkedans.correct == true){
               this.$store.state.Score++;
              }
              alert(this.$store.state.Score) */

            }
        },
        created () {
            this.countDownTimer(),
            this.initData()
        }
    }
    
</script>

<style scoped lang="less">
</style>

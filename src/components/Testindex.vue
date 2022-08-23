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
                }else{

             this.initData(this.idQ)
                }
            },
            initData(indexedId){
              this.listD=this.$store.state.dataListe[indexedId]
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
            
             // this.idQ++
             // alert('/inTest/'+this.idQ)
             
              if(this.idQ == 5){
                this.$router.push({name:'ResultScore'})
              }


             this.initData(this.idQ)
             //  if(this.$route.path != "/inTest/'+this.idQ"){
              // this.$router.push({name:'intest',params: {id:this.idQ}}).catch(() => {})
             



              if(this.checkedans.correct == true){
               this.$store.state.Score++;
              }
            /*  alert(this.$store.state.Score) */

            }
        },
        created () {
            this.countDownTimer(),
            this.initData(this.idQuestion)
        } /*,
        watch: {
          $route: function(val) {
            this.initData()
            console.log(val)
          }
        } */
    }
    
</script>

<style scoped lang="less">
</style>

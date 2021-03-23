<template>
  <div class="container">
    <div class="title">
      <h1>Typing Game</h1>
      <div class="marker"></div>
    </div>
    <button v-if="startFlg!=true" class="startButton mb-20" @click="gameStart">START</button>
    <div v-if="startFlg">
      <div class="question mb-20">{{ current_question }}</div>
      <div v-if="current_question_counts == question_counts" class="clear">Clear!</div>
      <div class="typeformWapper mb-20">
        <input id="typeForm" v-model="typeBox" type="text" class="typeform">
      </div>
      <div class="gaugeWarapper mb-20">
        <div :style="styleObject" class="gauge"></div>
      </div>
      <div>{{ current_question_counts }}/{{ question_counts }}</div>
    </div>
  </div>
</template>

<script>
export default{
data(){
  return {
    startFlg: "",
    current_question: "",
    questions: [
      'apple',
      'banana',
      'chocolate',
      'donut',
      'espresso',
    ],
    typeBox: "",
    current_question_counts: 0,
    question_counts:0,
  }
},

computed:{
  styleObject:function(width,color){
    width = 20 * this.current_question_counts + "%"
    if(this.current_question_counts == 5){
      color = "#03a9f4"
    }else{
      color = "orange"
    }
    return{
      'width': width,
      'background-color': color
    }
  }
},

methods:{
  gameStart:function(){
    this.startFlg = true;
    this.$nextTick(function(){
      document.getElementById('typeForm').focus()
    })
  }
},

mounted: function(){
  this.current_question = this.questions[0]
  this.question_counts = this.questions.length
},

watch:{
  typeBox:function(e){
    if(e == this.current_question){
      this.questions.splice(0,1)
      this.current_question = this.questions[0]
      this.typeBox = ""
      this.current_question_counts += 1
    }
  }
}
}
</script>

<style>
  .mb-20{
    margin-bottom: 20px;
  }

.container{
  width: 400px;
  margin: 0 auto;
  text-align: center;
}

.title{
  position: relative;
  font-size: 48px;
}

.marker{
  width: 100%;
  height: 35%;
  background-color: #a2a2a270;
  position: absolute;
  bottom: 5%;
  z-index: -1;
}

.startButton{
  background-color: #333;
  color: #fff;
  padding: 4px 60px;
  border: none;
  outline: none;
  border-radius: 8px;
  cursor: pointer;
}

.startButton:hover{
  opacity: 0.7;
}

.question{
  color: gray;
}

.clear{
  color: #03a9f4;
}

.typeform{
  text-align: center;
  outline: none;
  border: none;
}

.typeformWapper{
  border-bottom: 1px solid gray;
}

.gauge{
  height: 12px;
  transition: all .3s ease;
}

.gaugeWarapper{
  border: 1px solid;
  height: 12px;
}
</style>
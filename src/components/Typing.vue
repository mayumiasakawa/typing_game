<template>
  <div class="container">
    <div class="title">
      <h1>Typing Game</h1>
      <div class="marker"></div>
    </div>
    <button class="startButton mb-20">START</button>
    <div class="question mb-20">apple</div>
    <div class="clear">Clear!</div>
    <div class="typeformWapper mb-20">
      <input type="text" class="typeform">
    </div>
    <div class="gaugeWarapper mb-20">
      <div class="gauge"></div>
    </div>
    <div>1/5</div>
  </div>
</template>

<script>
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
}

.gaugeWarapper{
  border: 1px solid;
  height: 12px;
}
</style>
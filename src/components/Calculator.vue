<template>
  <div id="Calculator">
    <p id="display">display</p>
    <p class = "btn">C</p>
    <p class = "btn">+/-</p>
    <p class = "btn">%</p>
    <p class="btn operator">/</p>
    <p class = "btn">9</p>
    <p class = "btn">8</p>
    <p class = "btn">7</p>
    <p class="btn operator">*</p>
    <p class = "btn">6</p>
    <p class = "btn">5</p>
    <p class = "btn">4</p>
    <p class="btn operator">-</p>
    <p class = "btn">3</p>
    <p class = "btn">2</p>
    <p class = "btn">1</p>
    <p class="btn operator" id="add">+</p>
    <p class = "btn" id="zero">0</p>
    <p class = "btn">.</p>
    <p class = "btn operator">=</p>

  </div>
</template>

<script>
export default {
  setup() {
    
  },
}
</script>

<style>
#Calculator{
  margin: auto;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: (50px, auto);
}
#display{
  grid-column: 1 / 5;
  background-color: blueviolet;
  text-align: right;
  
}
p{
  margin: 1px;
  padding: 40px;
  background-color: darkcyan;
  font-size: 30px;


}
.operator{
  background-color: chartreuse;
  display: flex;
  box-sizing: border-box;
  
}
#add{
  
}
#zero{
  grid-column: 1 /3;
}
</style>
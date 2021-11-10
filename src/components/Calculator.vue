<template>
  <div id="Calculator">
    <p id="display">{{ current }}</p>
    <p @click="clear" class = "btn">C</p>
    <p @click="sign" class = "btn">+/-</p>
    <p @click="percent" class = "btn">%</p>
    <p @click="divide" class="btn operator">/</p>
    <p @click="append('7')" class = "btn">7</p>
    <p @click="append('8')" class = "btn">8</p>
    <p @click="append('9')" class = "btn">9</p>
    <p @click="multiply" class="btn operator">*</p>
    <p @click="append('4')" class = "btn">4</p>
    <p @click="append('5')" class = "btn">5</p>
    <p @click="append('6')" class = "btn">6</p>
    <p @click="subtract" class="btn operator">-</p>
    <p @click="append('1')" class = "btn">1</p>
    <p @click="append('2')" class = "btn">2</p>
    <p @click="append('3')" class = "btn">3</p>
    <p @click="add" class="btn operator" id="add">+</p>
    <p @click="append('0')" class = "btn" id="zero">0</p>
    <p @click="dot" class = "btn">.</p>
    <p @click="equal" class = "btn operator">=</p>

  </div>
</template>

<script>
export default {
  data(){
    return {
      previous: null,
      current: '' | 0,
      operator: null,
      operatorClicked: false,
    }
  },
  methods:{
    clear(){
      this.current = 0;
    },
    sign(){
      this.current = this.current.charAt(0) === '-' ? 
      this.current.slice(1) : `-${this.current}`;
    },
    percent(){
      this.current = `${parseFloat(this.current)/100}`;
    },
    append(number){
      if (this.operatorClicked) {
        this.current = '';
        this.operatorClicked = false;
      }
      if (this.current == 0){
        this.current = '';
      }
      this.current = `${this.current}${number}`;
      
    },
    dot(){
      if (this.current.indexOf('.') === -1){
        this.append('.');
      }
    },
    setPrevious(){
      this.previous = this.current;
      this.operatorClicked = true;
    },
    divide(){
      this.operator = (a,b)=> a/b;
      this.setPrevious();
    },
    multiply(){
      this.operator = (a,b)=> a*b;
      this.setPrevious();
    },
    subtract(){
      this.operator = (a,b) => a-b;
      this.setPrevious();
    },
    add(){
      this.operator = (a,b) => a+b;
      this.setPrevious();
    },
    equal(){
      if (this.previous == null){
        this.current = parseFloat(this.current);
      }
      else{
      this.current = `${this.operator(parseFloat(this.previous), parseFloat(this.current))}`;
      this.previous = null;
      }
      
    }
  }

}
</script>

<style>
#Calculator{
  margin: 0 auto;
  width: 600px;
  height: 400px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: (40px, auto);
}
#display{
  grid-column: 1 / 5;
  background-color: blueviolet;
  text-align: right;
  font-size: 50px;
  height: 55px;
  
}
p{
  margin: 1px;
  padding: 20px;
  background-color: darkcyan;
  font-size: 30px;
  text-align: center;


}
.operator{
  background-color: chartreuse;
  text-align: center;
  
}

#zero{
  grid-column: 1 /3;
}
</style>
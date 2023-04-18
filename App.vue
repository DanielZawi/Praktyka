<template>
  <div class="screen screen--1">
        <p>{{ massOne }} {{ unitOne }}</p>
        <div class="btn--options">
          <button><img src="/image/picture1.png" alt=""></button>
          <button @click = "deafultValueOne"><img src="/image/picture2.png" alt=""></button>
          <button><img src="/image/picture3.png" alt=""></button>
        </div>
    </div>
    <div class="screen screen--2">
        <p>{{massTwo}}</p>
        <div class="btn--options">
          <button><img src="/image/picture1.png" alt=""></button>
          <button @click = "deafultValueTwo"><img src="/image/picture2.png" alt=""></button>
          <button><img src="/image/picture3.png" alt=""></button>
        </div>
    </div>
    <div class="screen screen--3">
        <p>{{massThree}}</p>
        <div class="btn--options">
          <button><img src="/image/picture1.png" alt=""></button>
          <button @click = "deafultValueThree"><img src="/image/picture2.png" alt=""></button>
          <button><img src="/image/picture3.png" alt=""></button>
        </div>
    </div>
    <div class="screen screen--4">
        <p>{{massFour}}</p>
        <div class="btn--options">
          <button><img src="/image/picture1.png" alt=""></button>
          <button @click = "deafultValueFour"><img src="/image/picture2.png" alt=""></button>
          <button><img src="/image/picture3.png" alt=""></button>
        </div>
    </div>
</template>

<script>

const ws = new WebSocket('ws://10.10.2.125:4101');
let json; 

const mass = [];
const unit = [];
const precision = [];




export default {
  name: 'App',
  data(){
    return{
      massOne: '----',
      massTwo: '----',
      massThree: '----',
      massFour: '----',
      unitOne: '',
      }
  },
  methods:{
    deafultValueOne(){
      this.massOne = 0 .toPrecision(precision[0]);
    },
    deafultValueTwo(){
      this.massTwo = 0 .toPrecision(precision[1]);
    },
    deafultValueThree(){
      this.massThree = 0 .toPrecision(precision[2]);
    },
    deafultValueFour(){
      this.massFour = 0 .toPrecision(precision[3]);
    },
},
mounted(){

function responseData(evt) {
    json = JSON.parse(evt.data);
} 

function getMass (item){
    let massValue = mass[item]
    return massValue;
}

// function getUnit (item){
//     let unitValue = unit[item]
//     return unitValue;
// }

  ws.addEventListener("open", () =>{
  
  console.log("We are connected!");
  setInterval(function(){
    ws.send('{"COMMAND" : "GET_MASS"}')
  }, 30000)
  
  setInterval(function(){
    ws.onmessage = function(evt) { 
      responseData(evt);
      for(let i = 0; i < 4; i++){
        precision[i] = json['NetAct']['Precision']; 
        mass[i] = Number(json['NetAct']['Value']).toPrecision(precision[i]);
        unit[i] = json['NetAct']['Unit'];    
      }
    }
    console.log(mass)
    console.log(getMass(0))

    this.massOne = getMass(0)
    this.massTwo = getMass(1)
    this.massThree = getMass(2)
    this.massFour = getMass(3)

    console.log(this.massOne)

  }, 30000) 


});   
}
}
</script>

<style>
  @import './assets/css/style.css';
</style>

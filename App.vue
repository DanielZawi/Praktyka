<template>
  <div class="screen screen--1">
        <p>{{massOne}} {{unit}}</p>
        <div class="btn--options">
          <button @click = "randomMassOne"><img src="/image/picture1.png" alt=""></button>
          <button @click = "deafultValueOne"><img src="/image/picture2.png" alt=""></button>
          <button @click = "randomMassOne"><img src="/image/picture3.png" alt=""></button>
        </div>
    </div>
    <div class="screen screen--2">
        <p>{{massTwo}} {{unit}}</p>
        <div class="btn--options">
          <button @click = "randomMassTwo"><img src="/image/picture1.png" alt=""></button>
          <button @click = "deafultValueTwo"><img src="/image/picture2.png" alt=""></button>
          <button @click = "randomMassTwo"><img src="/image/picture3.png" alt=""></button>
        </div>
    </div>
    <div class="screen screen--3">
        <p>{{massThree}} {{unit}}</p>
        <div class="btn--options">
          <button @click = "randomMassThree"><img src="/image/picture1.png" alt=""></button>
          <button @click = "deafultValueThree"><img src="/image/picture2.png" alt=""></button>
          <button @click = "randomMassThree"><img src="/image/picture3.png" alt=""></button>
        </div>
    </div>
    <div class="screen screen--4">
        <p>{{massFour}} {{unit}}</p>
        <div class="btn--options">
          <button @click = "randomMassFour"><img src="/image/picture1.png" alt=""></button>
          <button @click = "deafultValueFour"><img src="/image/picture2.png" alt=""></button>
          <button @click = "randomMassFour"><img src="/image/picture3.png" alt=""></button>
        </div>
    </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return{
      massOne: 0,
      massTwo: 0,
      massThree: 0,
      massFour: 0,
      unit: 'g'
    }
  },
  methods:{
    deafultValueOne(){
      this.massOne = 0 .toPrecision(5);
    },
    deafultValueTwo(){
      this.massTwo = 0 .toPrecision(5);
    },
    deafultValueThree(){
      this.massThree = 0 .toPrecision(5);
    },
    deafultValueFour(){
      this.massFour = 0 .toPrecision(5);
    },
    generateNumber: function(){
      let mass = Math.random() * 100
      return mass.toPrecision(5)
    },
    randomMassOne(){
      this.massOne = this.generateNumber(); 
    },
    randomMassTwo(){
      this.massTwo = this.generateNumber(); 
    },
    randomMassThree(){
      this.massThree = this.generateNumber(); 
    },
    randomMassFour(){
      this.massFour = this.generateNumber(); 
    }
  },
  mounted() {	
    this.massOne = this.generateNumber(); 
    this.massTwo = this.generateNumber();  
    this.massThree = this.generateNumber(); 
    this.massFour = this.generateNumber();    
   }
}
</script>

<style>
  @import './assets/css/style.css';
</style>

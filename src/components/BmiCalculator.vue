<script>
export default {
  name: 'BmiCalculator',
  
  data() {
    return {
      mass: '',
      height: '',
      feet: '',
      inc: '',
      result: '',
      metric: {
        mass: 'kg',
        height: 'cm',
        select: false
      },
      us: {
        mass: 'libras',
        height: 'feet',
        select: false
      },
    }
  },
  methods: {
    calculateBmi() {
      if(this.metric.select){
        // + operator for converting string to number
        const bmi = +(this.mass / Math.pow((this.height/100), 2)).toFixed(1) 
        if(this.mass === '' || this.height === '') {
          alert('Favor preencher os campos!')
        }else if(this.mass <= 0 || this.height <= 0){
          alert('Valores não podem ser negativos!')
        }
        if(bmi < 18.5 && bmi > 0) {
          this.result = 'Abaixo do peso'
        }else if(bmi >=18.5 && bmi < 24.9) {
          this.result = 'Normal'
        }else if(bmi >=24.9 && bmi < 29.9) {
          this.result = 'Acima do peso'
        }else if(bmi >= 29.9){
          this.result = 'Obeso'
        }
      
      }else{
        const cm = (this.feet * 30.48 + this.inc * 2.54)
        const kg = this.mass * 0.4535923
        const bmi = +(kg/ Math.pow((cm/100), 2)).toFixed(1)
        if(this.mass === '' || this.feet === '' || this.inc === '') {
          alert('Favor preencher os campos')
        }else if(this.mass <= 0 || this.feet <= 0 || this.inc <= 0 ){
          alert('Valores não podem ser negativos!')
        }
        if(bmi < 18.5 && bmi > 0) {
          this.result = 'Abaixo do peso'
        }else if(bmi >=18.5 && bmi < 24.9) {
          this.result = 'Normal'
        }else if(bmi >=24.9 && bmi < 29.9) {
          this.result = 'Acima do peso'
        }else if(bmi >= 29.9){
          this.result = 'Obeso'
        }
      }
    },
    selectMetric() {
      this.metric.select = !this.metric.select
      this.us.select = false
      this.result = ''
      this.mass = ''
      this.height = ''
    },
    selectUs() {
      this.us.select = !this.us.select
      this.metric.select = false
      this.result = ''
      this.mass = ''
      this.feet = ''
      this.inc = ''
    },
  }
}
</script>

<template>
  <section class="container">
    <div class="options">
      <button @click="selectMetric">Metros/KG</button>
      <button @click="selectUs">Libras/Pés</button>
    </div>
    

    <form v-if="metric.select">
      <label>Peso( kg )</label>
      <input type="number" v-model="mass" :placeholder="metric.mass">
      <label>Altura ( cm )</label>
      <input type="number" v-model="height" :placeholder="metric.height">
      <button class="calculate" @click.prevent="calculateBmi">Calcular</button>
    </form>

    <form v-if="us.select">
      <label>Peso ( libras )</label>
      <input type="number" v-model="mass" :placeholder="us.mass">
      <label>Altura( pés.polegadas )</label>
      <input type="number" v-model="feet" placeholder="pés">
      <input type="number" v-model="inc" placeholder="polegas">
      <button class="calculate" @click.prevent="calculateBmi">Calcular</button>
    </form>
    
    <h1>{{ result }}</h1>
  </section>
</template>


<style scoped>
html,* {
  font-size: x-large;
}
.container {
  display: flex;
  width: 60vh;
  margin: 0 auto;
  flex-direction: column;
  justify-content: space-between;
  align-items: center;
  padding: 10vh;
  border-radius: 2vh;
  background: rgb(56, 88, 179);
  background: linear-gradient(119deg, rgba(121, 151, 233, 0.194) 31%, rgba(87, 66, 180, 0.169) 70%);
}
.options {
  margin: 0 auto;
  width: 50vh;
  display: flex;
  justify-content: space-around;
}
button{
  height: 8vh;
  width: 18vh;
  border-radius: 1vh;
  font-size: 3vh;
  font-weight: 600;
  background-color: whitesmoke;
  color: #2c3e50;
}
button:focus {
  color: whitesmoke;
  background-color: #2c3e509f;
}
form {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 5vh;
  color: black;
}
.calculate {
  margin-top: 2vh;
}
@media (max-width: 500px) {
  .container, * {
    max-width: 40vh;
  }
}
</style>
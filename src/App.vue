<template>
  <div id="app">
    <h4>Zadatak 1</h4>
    <div v-for="(animal, i) in AnimalList" :key="i">{{ animal.type }} / {{ animal.name }} / {{animal.datumRodjenja }}</div>

    <h4>Zadatak 2 ternary operator</h4>
    <div v-for="(animal, i) in AnimalList" :key="i">{{ animal.type }} / {{ animal.name }} / {{animal.datumRodjenja ? animal.datumRodjenja : 'nepozntaoTernary' }}</div>

    <h4>Zadatak 2 sa metodama</h4>
    <div v-for="(animal, i) in AnimalList" :key="i">{{ animal.type }} / {{ animal.name }} / {{ renderBirthday(animal) }}</div>
  </div>
</template>

<script>


export default {
  name: 'App',
  data(){
    return {
      AnimalList: [
        {
          type: 'Zirafa',
          name: 'Jedinica',
          datumRodjenja: new Date(),
        },
        {
          type: 'Panter',
          name: 'Dvojka',
          datumRodjenja: new Date(),
        },
        {
          type: 'Lav',
          name: 'Trojka',
          datumRodjenja: new Date(),
        },
        {
          type: 'Slon',
          name: 'Cetvorka',
        },
        {
          type: 'Tigar',
          name: 'Petica',
        },
      ],
    }
  },

  methods: {
    renderBirthday(animal){
      return animal.datumRodjenja || 'Nepoznato'
    }
  }
  
}
</script>

<style>

</style>

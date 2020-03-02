<template>
  <div id="app">
    <h4>Zadatak 1</h4>
    <div v-for="(animal, i) in AnimalList" :key="i">{{ animal.type }} / {{ animal.name }} / {{animal.datumRodjenja }}</div>


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
          datumRodjenja: new Date(),
        },
        {
          type: 'Tigar',
          name: 'Petica',
          datumRodjenja: new Date(),
        },
      ],
    }
  }
  
}
</script>

<style>

</style>

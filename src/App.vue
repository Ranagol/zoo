<template>
  <div id="app">
    <h4>Zadatak 1</h4>
    <table class="table">
      <tr>
        <th>Type</th>
        <th>Name</th>
        <th>datumRodjenja</th>
      <tr v-for="animal in AnimalList" :key="animal.name">
        <td>{{ animal.type }}</td>
        <td>{{ animal.name }}</td>
        <td>{{animal.datumRodjenja ? animal.datumRodjenja : 'nepozntaoTernary'  }}</td>
        <td><button class="btn btn-info" @click="removeAnimal(animal)">Remove</button></td>
        <td><button class="btn btn-info">Move to top</button></td>
      </tr>
    </table>


    <!--
    <h4>Zadatak 2 sa metodama</h4>
    <div v-for="(animal, i) in AnimalList" :key="i">{{ animal.type }} / {{ animal.name }} / {{ renderBirthday(animal) }}</div>
    -->
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
      return animal.datumRodjenja || 'Nepoznato'//vrati datumRodjenja, a ako to nema, onda vrati 'Nepoznato'
    },
    removeAnimal(animal){
      const index = this.AnimalList.indexOf(animal);
      console.log(index);
      this.AnimalList.splice(index, 1);
    }
  }
  
}
</script>

<style>

</style>

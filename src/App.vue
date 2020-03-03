<template>
  <div id="app" class="container">
    <h2>Zoo</h2>

    <form>
      <select class="form-group" v-model="type">
        <option disabled value="">Please select one</option>
        <option>Zmija</option>
        <option>Ptica</option>
        <option>Sisar</option>
      </select>
      <span>type: {{ selected }}</span>
      <br>

      <input v-model="name" type="text" class="form-group" placeholder="name"><br>

      <input v-model="datumRodjenja" type="text" class="form-group" placeholder="datumRodjenja"><br>

      <button @click.prevent="addAnimal" class="btn btn-success form-group">Create animal</button>
    </form>


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
        <td><button class="btn btn-info" @click="moveToTop(animal)" >To top</button></td>
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
      type:'',
      name:'',
      datumRodjenja:'',
      AnimalList: [
        {
          type: 'Zirafa',
          name: 'Jedinica',
          datumRodjenja: '22.12.2019',
        },
        {
          type: 'Panter',
          name: 'Dvojka',
          datumRodjenja: '22.12.2018',
        },
        {
          type: 'Lav',
          name: 'Trojka',
          datumRodjenja: '22.12.2017',
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
      //console.log(index);
      this.AnimalList.splice(index, 1);
    },
    moveToTop(animal){
      const index = this.AnimalList.indexOf(animal);
      //console.log(index);
      this.AnimalList.splice(index, 1);
      this.AnimalList.unshift(animal);
    },
    createAnimal(){
      return { type: this.type, name: this.name, datumRodjenja: this.datumRodjenja }
    },
    addAnimal(){
      this.AnimalList.push(this.createAnimal());
    }
  }
  
}
</script>

<style>

</style>

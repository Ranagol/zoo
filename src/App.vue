<template>
  <div id="app" class="container">
    <h1>Zoo</h1>
    <hr>
    <h3>Create new animal</h3>
    <form>
      <input v-model="type" type="text" class="form-group" placeholder="type"><br>
      <input v-model="name" type="text" class="form-group" placeholder="name"><br>

      <select v-model="sektor" class="form-group">
        <option v-for="(option2, i) in options2" :key="i" v-bind:value="option2.value">
          {{ option2.text }}
        </option>
      </select>
      <br>
      
      <input v-model="datumRodjenja" type="text" class="form-group" placeholder="datumRodjenja"><br>
      <button @click.prevent="addAnimal" class="btn btn-success form-group">Create animal</button>
    </form>
    <hr>

    <h3>AnimalList</h3>
    <table class="table">
      <tr>
        <th>Type</th>
        <th>Name</th>
        <th>Sektor</th>
        <th>datumRodjenja</th>
      <tr v-for="animal in AnimalList" :key="animal.name">
        <td>{{ animal.type }}</td>
        <td>{{ animal.name }}</td>
        <td>{{ animal.sektor }}</td>
        <td>{{animal.datumRodjenja ? animal.datumRodjenja : 'nepozntaoTernary'  }}</td>
        <td><button class="btn btn-danger" @click="removeAnimal(animal)">Remove</button></td>
        <td><button class="btn btn-info" @click="moveToTop(animal)" >To top</button></td>
      </tr>
    </table>
    <hr>

    <h3>Tabela sektora</h3>
    <table class="table">
      <tr>
        <th>Sektor</th>
        <th>Prikazi</th>
      </tr>
      <tr v-for="(option2, i) in options2" :key="i">
        <td>{{ option2.text }}</td>
        <td><button @click="prikazi(option2.text)" class="btn btn-warning">Prikazi</button></td>
      </tr>
    </table>
  </div>
</template>

<script>


export default {
  name: 'App',
  data(){
    return {
      sektor: 'Europe',
      options2: [
        { text: 'Europe', value: 'Europe' },
        { text: 'Asia', value: 'Asia' },
        { text: 'Africa', value: 'Africa' }
       ],

      type:'',
      name:'',
      datumRodjenja:'',
      AnimalList: [
        {type: 'Zirafa', name: 'Jedinica', sektor: 'Europe', datumRodjenja: '22.12.2019',},
        {type: 'Panter', name: 'Dvojka', sektor: 'Asia', datumRodjenja: '22.12.2018',},
        {type: 'Lav', name: 'Trojka', sektor: 'Africa', datumRodjenja: '22.12.2017',},
        {type: 'Slon', name: 'Cetvorka', sektor: 'Africa',},
        {type: 'Tigar', name: 'Petica', sektor: 'Asia',},
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
      return { type: this.type, name: this.name, sektor: this.sektor, datumRodjenja: this.datumRodjenja }
    },
    addAnimal(){
      this.AnimalList.push(this.createAnimal());
    },
    prikazi(text){
      let newArray = this.AnimalList.filter(function(animal){
        return animal.sektor == text;
      })
      alert(JSON.stringify(newArray));
    }

    
    
  }
  
}
</script>

<style>

</style>

<template>
  <div class="hello">
    <h2> Dodaj Zivotinju </h2>
    <form method="POST" @submit.prevent="addAnimal"> 
      <input v-model="ime" placeholder="unesi ime">
      <input v-model="vrsta" placeholder="unesi vrstu">
      <input v-model="datumRodjenja" type="date" >
      <button>Add Animal</button>
    </form>


    <p>Lista Zivotinja:</p>

    <table>
      <tr> 
        <td>Vrsta</td>
        <td>Ime</td>
        <td>Datum</td>
        <td>Brisanje zivotinje</td>
        <td>Move</td>
      </tr>
      <tr v-for="(animal,index) in animals" :key="index">
        <td>{{ animal.vrsta }}</td>
        <td>{{ animal.ime }}</td>
        <td v-if="animal.datumRodjenja">{{ animal.datumRodjenja }}</td>
        <td v-else> Nepoznato </td>
        <td><button @click="izbrisatiZivotinju(index)">Remove</button></td>
        <td><button @click="moveToTop(index, animal)">Move To Top</button></td>

      </tr>
    </table>

  </div>
</template>

<script>
export default {
  name: 'AnimalList',
  data () {
  return {
  
  animals: [
        { vrsta: "Pas", ime: "Mica", datumRodjenja: new Date().toLocaleString() },
        { vrsta: "Medved", ime: "Balu", datumRodjenja: new Date().toLocaleString() },
        { vrsta: "Oro", ime: "Mimi", datumRodjenja: new Date().toLocaleString()},
        { vrsta: "Delfin", ime: "Pero", datumRodjenja: new Date().toLocaleString() },
        { vrsta: "Macka", ime: "Cile " }
  ],
  vrsta: '',
  ime: '',
  datumRodjenja: null,
  

  }

  },

  methods: {
    izbrisatiZivotinju(index) {
        this.animals.splice(index, 1);
    },

    moveToTop(index, animal) {
      this.izbrisatiZivotinju(index);
      this.animals.unshift(animal);
    },

    addAnimal() {
      var newAnimal = {
        ime: this.ime,
        vrsta: this.vrsta,
        datumRodjenja: this.datumRodjenja,
      }
      this.animals.push(newAnimal);
      this.ime ='';
      this.vrsta= '';
      this.datumRodjenja= null;
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}


table td {
width: 100px;
}

table {
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
}

td {
  padding: 8px;
  text-align: left;
  border-bottom: 1px solid #ddd;
}

tr:hover {background-color: green;
  cursor: pointer;
}

button {
  border: none;
  border-radius: 5px;
  background-color: red;
  color: white;
  width: 200px;
}
form {
  display: flex;
  flex-direction: column;
}
form input {
  width: 200px;
}
</style>

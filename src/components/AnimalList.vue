<template>
  <div class="hello">
    
    <p>Lista Zivotinja:</p>
  <div class="table">
    <table>
      <tr> 
        <td>Vrsta</td>
        <td>Ime</td>
        <td>Datum</td>
      </tr>
      <tr v-for="(animal,index) in animals" :key="index">
        <td>{{ animal.vrsta }}</td>
        <td>{{ animal.name }}</td>
        <td v-if="animal.datumRodjenja">{{ animal.datumRodjenja }}</td>
        <td v-else> Nepoznato </td>
  

      </tr>
    </table>
</div>
  </div>
</template>

<script>
export default {
  name: 'AnimalList',
  data () {
  return {
  
  animals: [
        { vrsta: "Pas", name: "Mica", datumRodjenja: new Date().toLocaleString() },
        { vrsta: "Medved", name: "Balu", datumRodjenja: new Date().toLocaleString() },
        { vrsta: "Oro", name: "Mimi"},
        { vrsta: "Delfin", name: "Pero", datumRodjenja: new Date().toLocaleString() },
        { vrsta: "Macka", name: "Cile " }
  ],


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
</style>

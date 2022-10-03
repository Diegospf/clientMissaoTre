<template>
  <div id="app">
    <NavBar @mudarTipo="mudarTipo($event)"/>
    <TableMenu :msg= this.tipo></TableMenu>
  </div>
</template>

<script>
import axios from 'axios'
import NavBar from './components/NavBar'
import TableMenu from './components/TableMenu'

export default {
  name: 'App',
  data () {
    return {
      info: null,
      tipo: "Zona"
    }
  },
  components: {
    NavBar,
    TableMenu
},
methods: {
   mudarTipo (tipo) {
     this.tipo = tipo;
   }
},
  mounted(){
    axios
      .get('http://localhost:8082/search/polo/1')
      .then(response => (this.info = response.data))
      .catch(error => console.log(error))
  }
}
</script>

<style>
#app {
  max-width: 1230px;
  min-width: 300px;
  margin-left: auto;
  margin-right: auto;
  height: 100vh;
  background-color: cadetblue;
}
</style>

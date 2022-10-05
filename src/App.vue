<template>
  <div id="app">
    <NavBar @mudarTipo="mudarTipo($event)"/>
    <TableMenu :msg= this.tipo @pesquisar="pesquisar($event)" @tipoPesquisa="tipoPesquisa($event)"></TableMenu>
    <TableComponent :json= this.json :tipo= this.pesquisaSelecionadoTipo :alterado= this.alterado></TableComponent>
  </div>
</template>

<script>
import axios from 'axios'
import NavBar from './components/NavBar'
import TableMenu from './components/TableMenu'
import TableComponent from './components/TableComponent'

export default {
  name: 'App',
  data () {
    return {
      pesquisaSelecionado: "y",
      pesquisaSelecionadoTipo: "x",
      tipo: "Zona",
      alterado: true,
      info:'http://localhost:8082/search/polo/',
      json: null
    }
  },
  components: {
    NavBar,
    TableMenu,
    TableComponent
},
  methods: {
    mudarTipo (tipo) {
      this.tipo = tipo;
      this.alterado = true;
      this.json = '';
    },
    pesquisar(selecionado) {
        this.pesquisaSelecionado = selecionado;
    },
    tipoPesquisa(selecionadoTipo) {
        this.pesquisaSelecionadoTipo = selecionadoTipo;
        this.alterado = false;
        this.requestApi()
    },
    requestApi(){
      var tipo
      if(this.tipo == "Zona")
        tipo = "zona"
      if(this.tipo == "Polo")
        tipo = "polo"
      if(this.tipo == "Município")
        tipo = "municipio"
      this.info = 'http://localhost:8082/search/' + tipo + '/' + this.pesquisaSelecionadoTipo + '/' + this.pesquisaSelecionado;
      axios
        .get(this.info)
        .then(response => (this.json = response.data))
        .catch(error => console.log(error))
    }
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

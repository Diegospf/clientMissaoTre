<template>
    <div>
        <div class="container m-2">
            <div class="card mb-3 col-md-8 col-lg-5">
              <div class="card-header d-flex justify-content-between">
                <div>Consultar por {{msg}}: </div>
              </div>
              <div class="card-body mx-auto pb-4">
                <form>
                  <div class="d-flex align-items-start row mx-0">
                    <div class="px-0 mb-0 pt-1 pb-1 text-left rounded-top">
                      Escolha por {{msg}}:
                    </div>
                    <select v-if="msg=='Zona'" class="mt-0 form-select form-select-sm form-control" name="stockType" aria-label="Default select example rounded-3">
                      <option selected disabled hidden>Selecione a {{msg}}</option>
                      <option v-for="zona in todasZonas" :key="zona">  {{ zona }} </option>
                    </select>
                    <select v-if="msg=='Município'" class="mt-0 form-select form-select-sm form-control" name="stockType" aria-label="Default select example rounded-3">
                      <option selected disabled hidden>Selecione o {{msg}}</option>
                      <option v-for="municipio in todosMunicipios" :key="municipio">  {{ municipio.id }} - {{municipio.nome}} </option>
                    </select>
                    <select v-if="msg=='Polo'" class="mt-0 form-select form-select-sm form-control" name="stockType" aria-label="Default select example rounded-3">
                      <option selected disabled hidden>Selecione o {{msg}}</option>
                      <option v-for="polo in todosPolos" :key="polo">  {{ polo }} </option>
                    </select>
                    <div class="px-0 mt-3 mb-0 pt-1 pb-1 text-left rounded-top">
                      Escolha a pesquisa:
                    </div>
                    <select v-if="msg=='Zona'" class="mt-0 form-select form-select-sm form-control" name="stockType" aria-label="Default select example rounded-3">
                      <option th:value="none" selected disabled hidden>Selecione o resultado que espera</option>
                      <option  th:value="todos">Informações completas</option>
                      <option  th:value="sede">Municipio Sede</option>
                      <option  th:value="municipios">Todos os municípios</option>
                      <option  th:value="secoes">Quantidade de Seções</option>
                    </select>
                    <select v-if="msg=='Município'" class="mt-0 form-select form-select-sm form-control" name="stockType" aria-label="Default select example rounded-3">
                      <option th:value="none" selected disabled hidden>Selecione o resultado que espera</option>
                      <option  th:value="todos">Informações completas</option>
                      <option  th:value="secao">Quantidade de seções</option>
                      <option  th:value="zona">Todas as zonas</option>
                    </select>
                    <select v-if="msg=='Polo'" class="mt-0 form-select form-select-sm form-control" name="stockType" aria-label="Default select example rounded-3">
                      <option th:value="none" selected disabled hidden>Selecione o resultado que espera</option>
                      <option  th:value="todos">Informações completas</option>
                      <option  th:value="municipio">Todos os município</option>
                      <option  th:value="secao">Quantidade de seções</option>
                      <option  th:value="zona">Todas as zonas</option>
                      <option th:value="sede">Município Sede</option>
                    </select>
                    <div class="d-grid gap-2 col-4 px-0">
                      <button type="submit" class="mt-4 btn btn-warning">Pesquisar</button>
                    </div>
                  </div>
                </form>
              </div>
            </div> 
        </div>  
    </div>
    
</template>

<script>
    import axios from 'axios'
    export default{
        data () {
            return {
                todosMunicipios: null,
                todasZonas: null,
                todosPolos: null
            }
        },
        name:'TableMenu',
        props:{
            msg:String,
            information: Request
        },
        mounted(){
            axios.all([
                axios
                .get('http://localhost:8082/search/todosMunicipios')
                .then(response => (this.todosMunicipios = response.data))
                .catch(error => console.log(error)), 
                axios
                .get('http://localhost:8082/search/todosPolos')
                .then(response => (this.todosPolos = response.data))
                .catch(error => console.log(error)),
                axios
                .get('http://localhost:8082/search/todasZonas')
                .then(response => (this.todasZonas = response.data))
                .catch(error => console.log(error))
            ]);
        }
        
    }
    
</script>

<style scoped>

</style>
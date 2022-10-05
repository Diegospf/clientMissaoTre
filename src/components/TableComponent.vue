<template>
    <div v-if="this.alterado == false" class="mx-4">
      <b-table sticky-header v-if="this.tipo == 'todos' || this.tipo == 'secao' " striped hover :items= [this.json]  :fields="fieldsQnt" class="m-0"></b-table>
      <b-table sticky-header v-if="this.tipo == 'todos' || this.tipo == 'sede' " striped hover :items= [this.json] :fields="fieldsSede" class="m-0"></b-table>
      <b-table sticky-header v-if="this.tipo == 'municipio' " striped hover :items= this.json :fields="fieldsMunicipio" class="m-0"></b-table> 
      <b-table sticky-header v-if="this.tipo == 'zona' " striped hover :items= this.json :fields="fieldsZona" class="m-0"></b-table> 
      <b-table sticky-header v-if="this.tipo == 'todos' " striped hover :items= this.json.zonas :fields="fieldsTodos" class="m-0"></b-table> 
    </div>
  </template>
  
  <script>
    export default {
      data() {

        return {
            pesquisa: null,
            tipoPesquisa: null,
            like: this.json,
            fieldsSede: [
            {
                key: 'sede',
                variant: 'light'
            },
            {
                key: 'nomeSede',
                label: 'Nome',
                variant: 'light'
            }
            ],
            fieldsQnt: [
            {
                key: 'qntSecoes',
                label: 'Quantidade Seções',
                variant: 'light'
            }
            ],
            fieldsMunicipio: [
            {
                key: 'codTse',
                label: 'Código TSE',
                variant: 'light'
            },{
                key: 'nomeMun',
                label: 'Nome',
                variant: 'light'
            }
            ],
            fieldsZona: [
              {
                key: 'zona',
                label: 'Zona',
                variant: 'light'
            },
            {
                key: 'codTse',
                label: 'Código TSE',
                variant: 'light'
            },{
                key: 'nomeMun',
                label: 'Nome',
                variant: 'light'
            }
            ],
            fieldsTodos: [
              {
                key: 'zona',
                label: 'Zona',
                variant: 'light'
            },
            {
                key: 'codTse',
                label: 'Código TSE',
                variant: 'light'
            },{
                key: 'nomeMun',
                label: 'Nome',
                variant: 'light'
            }
            ]
        }
    },
    props:{
            json:String,
            tipo: String,
            alterado: Boolean,
            information: Request
        }
    }
  </script>

  <style scoped>
  .table-responsive {
    overflow-y: scroll;
    max-height: 10vh;
  }
  </style>
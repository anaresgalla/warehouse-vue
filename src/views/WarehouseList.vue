<template>
  <div>
    <h1>Galpões Cadastrados</h1>

    <v-text-field label="Buscar Galpão" v-model="term" class="my-5"></v-text-field>
    <v-card dark>
      <v-card-text>
        <WarehouseTable :warehouses="filterWarehouse"/>
      </v-card-text>
    </v-card>
  </div>
</template>

<script>

//importar o componente warehouse
import Warehouse from '../components/Warehouse.vue';

import WarehouseTable from '@/components/WarehouseTable.vue';

export default {
  name: 'WarehouseList',
  components: {
    Warehouse,
    WarehouseTable
  },

  data(){
    return{
      warehouses:[],
      term: ""
    }
  },

  async mounted(){
    this.getWarehouses();
  },

  methods:{
    async getWarehouses(){
      //Realizando a requisição
      const response = await this.$http.get('http://localhost:3000/api/v1/warehouses');
      const result = await response.json();
      //Exibindo os dados no console do computador
      console.log(result);
      //Adicionando os dados de result no array de warehouses
      this.warehouses = result;
      return this.warehouses;
    }
  },

  computed:{
    filterWarehouse(){
      return this.warehouses.filter(warehouse => {
        return warehouse.name.toLowerCase().includes(this.term.toLowerCase());
      })
    }
  }

}
</script>

<style>
  .form{
    margin-bottom: 20px;
  }
</style>
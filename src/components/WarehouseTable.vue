<template>
  <v-simple-table>
    <thead>
      <tr>
        <th>Nome</th>
        <th>Código</th>
        <th>Endereço</th>
        <th>Cidade</th>
        <th>Área</th>
        <th>Descrição</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="w in warehouses" :key="w.id">
        <td>{{w.name}}</td>
        <td>{{w.code}}</td>
        <td>{{w.address}}</td>
        <td>{{w.city}}</td>
        <td>{{w.area}}</td>
        <td>{{w.description}}</td>
      </tr>
    </tbody>
  </v-simple-table>
</template>

<script>
  export default {
    name: 'WarehouseTable',
    props: {
      warehouses:[]
    }
  }
</script>

<style>

</style>
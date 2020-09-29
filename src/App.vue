<template>
  <div id="app">
    <h1>Guia de Clientes</h1>
    <div v-for="(cliente, index) in clientes" :key="cliente.id">
      <h4>{{ index + 1 }}</h4>
      <Cliente :cliente="cliente"/>
      <h4>Edição</h4>
      <input type="text" v-model='cliente.nome' />
      <input type="text" v-model='cliente.email' />
    </div>
  </div>
</template>

<script>

import Cliente from './components/Cliente'

export default {
  name: 'App',
  data(){
    return {
      clientes: [
        {
          id: 1,
          nome: "Rafael Pianaro",
          numero: 56,
          email: "rafaelpianaro@gmail.com",
          idade: 37,
        },
        {
          id: 2,
          nome: "Maria Maria",
          numero: 15,
          email: "maria@gmail.com",
          idade: 23,
        },
        {
          id: 3,
          nome: "João Maria",
          numero: 76,
          email: "joaomaria@gmail.com",
          idade: 40,
        }
      ]
    }
  },
  components: {
    Cliente
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

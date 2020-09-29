<template>
  <div id="app">
    <h3>Cadastro</h3>
    <small class="erro" v-show="deuErro">Campo inválido</small><br>
    <input type="text" placeholder="Nome" v-model="nomeField" /><br>
    <input type="text" placeholder="E-mail" v-model="emailField" /><br>
    <input type="number" placeholder="Idade" v-model="idadeField" /><br>
    <button @click="cadastrarUsuario($event)">Cadastrar</button>
    <div v-for="(cliente, index) in clientes" :key="cliente.id">
      <h4>{{ index + 1 }}</h4>
      <Cliente :cliente="cliente"/>
    </div>
  </div>
</template>

<script>

import Cliente from './components/Cliente'

export default {
  name: 'App',
  data(){
    return {
      deuErro: false,
      nomeField: '',
      emailField: '',
      idadeField: 0,
      clientes: [
        {
          id: 1,
          nome: "Rafael Pianaro",
          numero: 56,
          email: "rafaelpianaro@gmail.com",
          idade: 37,
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
  },
  methods: {
    cadastrarUsuario: function(){
      if(this.nomeField == '' || this.nomeField == ' ' || this.nomeField.length < 3){
        this.deuErro = true
      }else{
        this.clientes.push({nome: this.nomeField, email: this.emailField, idade: this.idadeField, id: Date.now()})
        this.nomeField = '',
        this.emailField = '',
        this.idadeField = 0.
        this.deuErro = false
      }
    }
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
.erro{
  color: crimson;
}
</style>

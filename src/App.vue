<template>
  <div id="app">
    <h3>Cadastro</h3>
    <small class="erro" v-show="deuErro">Campo inválido</small><br>
    <input type="text" placeholder="Nome" v-model="nomeField" /><br>
    <input type="text" placeholder="E-mail" v-model="emailField" /><br>
    <input type="number" placeholder="Idade" v-model="idadeField" /><br>
    <button @click="cadastrarUsuario($event)">Cadastrar</button>
    <div v-for="(cliente, index) in orderClientes" :key="cliente.id">
      <h4>{{ index + 1 }}</h4>
      <Cliente :cliente="cliente" @meDelete='deletarUsuario($event)'/>
    </div>
  </div>
</template>

<script>
import _ from 'lodash'
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
          email: "rafaelpianaro@gmail.com",
          idade: 37,
        },
        {
          id: 3,
          nome: "João Maria",
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
        this.idadeField = 0,
        this.deuErro = false
      }
    },
    deletarUsuario: function($event) {
      console.log('recebendo evento')
      console.log($event.idCliente)
      var id = $event.idCliente
      var novoArray = this.clientes.filter(cliente => cliente.id != id)
      this.clientes = novoArray
      // $event.component.isPremium = true
    }
  },
  computed: {
    orderClientes(){
      // var c = this.clientes
      // console.log('lista',this.clientes)
      // var c = _.orderBy(this.clientes,['nome'],['asc'])
      // console.log('ordenado',c)
      return _.orderBy(this.clientes,['nome'],['asc'])
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

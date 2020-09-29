<template>
  <div :class="{'cliente': !isPremium,'cliente-premium' : isPremium}">
    <h4>Nome: {{ cliente.nome }}</h4>
    <p>Email: {{ cliente.email | processarEmail}}</p>
    <p v-if='showIdade === false'>Idade: {{ cliente.idade }}</p>
    <p v-else>Usuário escondeu a idade.</p>
    <button @click="mudarCor($event)">Mudar cor</button>
    <button @click="emitirEvendoDelete">Deletar</button>
    <h4>Id Especial: {{ idEspecial }}</h4>
  </div>
</template>

<script>
export default {
    data() {
        return {
            isPremium: false
        }
    },
    props: {
            cliente: Object,
            showIdade: Boolean
    },
    methods: {
        mudarCor: function($event){
            console.log($event)
            this.isPremium = !this.isPremium
        },
        emitirEvendoDelete: function(){
            console.log('emitindo do filho')
            this.$emit('meDelete',{idCliente: this.cliente.id,component: this})
        }
    },
    filters: {
        processarEmail(value){
            return value.toUpperCase()
        }
    },
    computed: {
        idEspecial(){
            return (this.cliente.email + this.cliente.nome + this.cliente.id).toUpperCase()
        }
    }
}
</script>

<style scoped>
    .cliente{
        background-color: bisque;
        max-width: 400px;
        height: 200px;
        padding: 10px;
        margin-top: 10px;
    }
    .cliente-premium{
        background-color: rgb(97, 97, 97);
        color: bisque;
        max-width: 400px;
        height: 200px;
        padding: 10px;
        margin-top: 10px;
    }
</style>
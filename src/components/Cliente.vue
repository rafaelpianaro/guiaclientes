<template>
  <div :class="{'cliente': !isPremium,'cliente-premium' : isPremium}">
    <h4>Nome: {{ cliente.nome }}</h4>
    <p>Número: {{ cliente.numero }}</p>
    <p>Email: {{ cliente.email }}</p>
    <p v-if='showIdade === true'>Idade: {{ cliente.idade }}</p>
    <p v-else>Usuário escondeu a idade.</p>
    <button @click="mudarCor($event)">Mudar cor</button>
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
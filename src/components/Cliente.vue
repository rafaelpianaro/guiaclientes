<template>
  <div id="cliente">
    <!-- <input type="text" v-model="nome">
    <h2>{{nome}}</h2>
    <h3>Descrição:</h3> -->
    <h4>Nome: {{ nome }}</h4>
    <p>{{ descricao }}</p>
    <p>Número: {{ numero }}</p>
    <p>Email: {{ email }}</p>
    <p>Idade: {{ idade }}</p>
  </div>
</template>

<script>
export default {
    data() {
        return {
            // nome: "Rafael Pianaro",
            numero: "99554 9171",
            email: "rafaelpianaro@gmail.com",
            idade: 37,
            descricao: "Lorem ipsun"
        }
    },
    props: {
            nome: String
        }
}
</script>

<style scoped>
    #cliente{
        background-color: bisque;
        max-width: 400px;
        height: 200px;
        padding: 10px;
        margin-top: 10px;
    }
</style>
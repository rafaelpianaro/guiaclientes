<template>
  <div id="cliente">
    <h4>Nome: {{ cliente.nome }}</h4>
    <p>Número: {{ cliente.numero }}</p>
    <p>Email: {{ cliente.email }}</p>
    <p v-if='showIdade === true'>Idade: {{ cliente.idade }}</p>
    <p v-else>Usuário escondeu a idade.</p>
  </div>
</template>

<script>
export default {
    data() {
        return {
            showIdade: true
        }
    },
    props: {
            nome: String,
            cliente: Object
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
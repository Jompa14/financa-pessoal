<template>
    <div id="app">
        <h1>Finança pessoal</h1>
        <tabela-usuario></tabela-usuario>
    </div>
</template>

<script>
import tabelaUsuario from './components/tabela.vue'
export default {
  name: 'App',
  components: {
      tabelaUsuario,
  }
};
</script>

<style scoped>
    #app {
        font-family: sans-serif;
        color: black;
    }
    h1 {
        color: #3ec8b3;
    }
</style>

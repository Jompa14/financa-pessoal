<template>
    <div id="app">
        <div class="navbar alinhamento">
            <h1>Finança pessoal</h1>
        </div>
        <painel-resumo></painel-resumo>
        <dash-usuario/>
        <tabela-usuario></tabela-usuario>
    </div>
</template>

<script>
import tabelaUsuario from './components/tabela.vue'
import painelResumo from './components/painelResumo.vue'
import dashUsuario from './components/dashUsuario.vue'
export default {
  name: 'App',
  components: {
      tabelaUsuario,
      painelResumo,
      dashUsuario,
  }
};
</script>
<!-- unico css da aplicação q tem css global -->
<style lang="scss">
    #app {
        font-family: sans-serif;
        color: black;
    }
    .alinhamento {
        width: 80%;
        max-width: 1800px;
        margin: 0 auto;
        @media(max-width: 600px){
            width: 90%;
        }
    }
    .navbar {
        display: flex;
        align-items: center;
        h1, h2, h3 {
            color: #3ec8b3;
        }
        // h2 {
        //     color: #3ec8b3;
        // }
    }
</style>

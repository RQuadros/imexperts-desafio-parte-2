<template>
  <div id="app" class="bg-cinza">
    <Cabecalho />
    <ListaUsuarios/>
  </div>
</template>
<script>
  import ListaUsuarios from './components/ListaUsuarios.vue'
  import Cabecalho from './components/Cabecalho.vue';  
  export default {
    components: {
      Cabecalho,
      ListaUsuarios
    }
  }
</script>
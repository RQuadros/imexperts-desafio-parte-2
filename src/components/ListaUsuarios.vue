<template>
  <div class="bg-cinza px-4">
    <TabelaUsuarios />
  </div>
</template>

<script>
import TabelaUsuarios from './TabelaUsuarios.vue'
export default {
  components: {
    TabelaUsuarios
  },
  data() {
    return {
      
    };
  },
};
</script>
<style>
  .bg-botao {
    background-color: #D83467!important;
  }
  .bg-gradient {
    background-image: linear-gradient(to right, #DE4059, #F97911);
  }
  .bg-cinza {
    background-color: #F5F5F5!important;
  }
</style>
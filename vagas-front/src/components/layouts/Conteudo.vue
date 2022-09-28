<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <h1>conteudo</h1>
  <Home></Home>
  <PublicarVaga></PublicarVaga>
</template>

<script>
import Home from '../views/Home.vue';
import PublicarVaga from '../views/PublicarVaga.vue';

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Conteudo',
  components: {
    Home,
    PublicarVaga,
  },
};
</script>

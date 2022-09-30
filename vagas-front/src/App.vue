<template>
  <div>
    <topo-padrao @navegar="componente = $event" />
    <conteudo v-if="visibilidade" :conteudo="componente"></conteudo>
  </div>
</template>

<script lang="ts">
import Conteudo from '@/components/layouts/Conteudo.vue';
import TopoPadrao from '@/components/layouts/Topo.vue';

export default {
  name: 'App',
  data: () => ({
    visibilidade: true,
    componente: 'ViewHome',
  }),
  components: {
    Conteudo,
    TopoPadrao,
  },
};
</script>

<style scoped></style>

<template>
  <div>
    <alerta></alerta>
    <vagas-favoritas></vagas-favoritas>
    <topo-padrao @navegar="componente = $event" />
    <conteudo v-if="visibilidade" :conteudo="componente"></conteudo>
  </div>
</template>

<script>
import Alerta from './components/comuns/Alerta.vue';
import Conteudo from '@/components/layouts/Conteudo.vue';
import TopoPadrao from '@/components/layouts/Topo.vue';
import VagasFavoritas from './components/comuns/VagasFavoritas.vue';


export default {
  name: 'App',
  data: () => ({
    visibilidade: true,
    componente: 'ViewHome',
  }),
  components: {
    Conteudo,
    TopoPadrao,
    VagasFavoritas,
    Alerta
  },
};
</script>

<style scoped></style>

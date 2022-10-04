<template>
  <div>
    <vagas-favoritas></vagas-favoritas>
    <topo-padrao @navegar="componente = $event" />
    <alerta v-if="exibirAlerta" :status="alerta.status">
      <template v-slot:titulo>
        <h5>{{ alerta.titulo }}</h5>
      </template>

      <div><p>------------</p></div>

      <template v-slot:descricao>
        <p>{{ alerta.descricao }}</p>
      </template>
    </alerta>
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
    exibirAlerta: false,
    alerta: { titulo: '', descricao: '' },
  }),
  components: {
    Conteudo,
    TopoPadrao,
    VagasFavoritas,
    Alerta,
  },
  mounted() {
    this.emitter.on('alerta', (event) => {
      this.alerta = event;
      this.exibirAlerta = true;
      setTimeout(() => {
        this.exibirAlerta = false;
      }, 3000);
    });
  },
};
</script>

<style scoped></style>

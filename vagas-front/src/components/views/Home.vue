<template>
  <div class="container py-4">
    <div class="row">
      <div class="col">
        <PesquisarVaga />
      </div>
    </div>
    <div class="row mt-5" v-for="(vaga, index) in vagas" :key="index">
      <div class="col">
        <Vagas v-bind="vaga" />
      </div>
    </div>
    <div class="row mt-5">
      <div class="col-4">
        <Indicador
          titulo="Vagas Abertas"
          :indicador="usuariosOnline"
          bg="bg-dark"
          color="text-white"
        />
      </div>
      <div class="col-4">
        <Indicador
          titulo="Profissionais Cadastrados"
          indicador="130"
          bg="bg-dark"
          color="text-white"
        />
      </div>
      <div class="col-4">
        <Indicador
          titulo="Visitantes Online"
          indicador="30"
          bg="bg-white"
          color="text-dark"
        />
      </div>
    </div>
  </div>
</template>

<script>
import PesquisarVaga from '@/components/comuns/PesquisarVaga.vue';
import Indicador from '@/components/comuns/Indicador.vue';
import Vagas from '@/components/comuns/Vaga.vue';
export default {
  name: 'ViewHome',
  components: { PesquisarVaga, Indicador, Vagas },
  data: () => ({
    usuariosOnline: 10,
    vagas: [],
  }),
  methods: {
    getUsuariosOnline() {
      this.usuariosOnline = Math.floor(Math.random() * 100);
    },
  },
  created() {
    setInterval(this.getUsuariosOnline, 1000);
  },
  activated() {
    this.vagas = JSON.parse(localStorage.getItem('vagas'));
  },
};
</script>

<style>
h1 {
  color: green;
}
</style>

<template>
  <div class="container py-4">
    <div class="row">
      <div class="col">
        <PesquisarVaga />
      </div>
    </div>
    <ListaVagas>
      <template v-slot:titulo="slotProps">
        <p>{{ slotProps.dadosTitulo.titulo }}</p>
      </template>
      <!-- <template v-slot:default="{ vagas }">
        <div v-for="(vaga, index) in vagas" :key="index">
          <h4>{{ vaga.titulo }}</h4>
          <p>{{ vaga.descricao }}</p>
          <hr />
        </div>
      </template> -->
      <template v-slot:rodape="slotProps">
        <p>{{ slotProps.dadosRodape.titulo }}</p>
      </template>
    </ListaVagas>

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
import ListaVagas from '@/components/comuns/ListaVagas.vue';

export default {
  name: 'ViewHome',
  components: { PesquisarVaga, Indicador, ListaVagas },
  data: () => ({
    usuariosOnline: 10,
  }),
  methods: {
    getUsuariosOnline() {
      this.usuariosOnline = Math.floor(Math.random() * 100);
    },
  },
  provide: {
    message: 'hello!',
  },
};
</script>

<style>
h1 {
  color: green;
}
</style>

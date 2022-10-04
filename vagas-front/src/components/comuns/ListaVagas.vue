<template>
  <slot name="titulo" :dadosTitulo="{ titulo: 'Titulo Lista', nroVagas: 15 }">
    <p>Titulo da Vaga</p>
  </slot>

  <slot atributo1="primeiro atributo encaminhado" :vagas="vagas">
    <div class="row mt-5" v-for="(vaga, index) in vagas" :key="index">
      <div class="col">
        <Vagas v-bind="vaga" />
      </div>
    </div>
  </slot>

  <slot
    name="rodape"
    :dadosRodape="{
      titulo: 'Rodape Lista',
      paginacao: { nroRodape: 10, paginaAtual: 1 },
    }"
  >
    <p>rodape da lista de vagas</p>
  </slot>
</template>

<script>
import Vagas from './Vaga.vue';

export default {
  name: 'ListaVagas',
  components: { Vagas },

  data: () => ({
    vagas: [],
  }),
  mounted() {
    console.log('mounted');
    this.emitter.on('filtrar', ({ titulo }) => {
      console.log(titulo);
      const vagas = JSON.parse(localStorage.getItem('vagas'));
      this.vagas = vagas.filter((e) =>
        e.titulo.toLowerCase().includes(titulo.toLowerCase())
      );
    });
  },
  activated() {
    console.log('active');
    this.vagas = JSON.parse(localStorage.getItem('vagas'));
  },
  methods: {},
};
</script>

<!-- eslint-disable vue/multi-word-component-names -->
<template>
  <div>
    <!-- <h1>{{ titulo }}</h1> -->
    <!-- <button @click="atualizarComponente()">Atualizar</button> -->
    <!-- <button @click="conteudo = 'home'">Home</button> -->
    <!-- <button @click="conteudo = 'publicar-vaga'">Publicar Vaga</button> -->
    <!-- renderizar de modo dinâmico os componentes home e publicar-vaga -->
    <!--<home></home>-->
    <!--<publicar-vaga></publicar-vaga>-->
    <keep-alive>
      <component :is="conteudo" />
    </keep-alive>
  </div>
</template>

<script>
import ViewHome from '../views/Home.vue';
import PublicarVaga from '../views/PublicarVaga.vue';

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Conteudo',
  props: {
    conteudo: String,
  },
  components: {
    ViewHome,
    PublicarVaga,
  },
  data: () => ({}),
};
</script>

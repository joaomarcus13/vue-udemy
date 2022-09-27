<template>
  <div>
    <h1>app</h1>
    <Topo />
    <Conteudo></Conteudo>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue';
import Conteudo from './components/layouts/Conteudo.vue';
import Topo from './components/layouts/Topo.vue';

export default {
  name: 'App',
  components: {
    Conteudo,
    Topo,
  },
};
</script>

<style scoped>
h1 {
  color: red;
}
</style>

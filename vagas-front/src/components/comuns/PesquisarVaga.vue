<template>
  <div class="h-100 p-5 bg-light border rounded-3">
    <h2>Pesquisar Vagas</h2>
    <div class="row">
      <div class="col">
        <div class="form-group">
          <label for="">Titulo da vaga</label>
          <input
            type="text"
            v-model="titulo"
            class="form-control"
            placeholder="Pesquise por palavras chaves, por exemplo 'PHP, 'Pleno', 'Analista'"
          />
          <small class="form-text text-muted"
            >Informe palavras que estejam relacionadas</small
          >
        </div>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <button
          class="btn btn-outline-dark mt-2"
          type="button"
          @click="pesquisar"
        >
          Buscar
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PesquisarVaga',
  inject: ['message'], //vinda de home
  created() {
    console.log(this.message); // injected value
    console.log(this.$data);
  },
  data: () => ({
    titulo: '',
  }),
  methods: {
    pesquisar() {
      console.log(this.titulo);
      this.emitter.emit('filtrar', {
        titulo: this.titulo,
      });
    },
  },
};
</script>

<style lang="scss" scoped></style>

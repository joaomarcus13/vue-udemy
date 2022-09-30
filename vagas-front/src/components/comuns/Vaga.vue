<template>
  <div class="card">
    <div class="card-header bg-dark text-white">{{ titulo }}</div>
    <div class="card-body">
      <p>{{ descricao }}</p>
    </div>
    <div class="card-footer">
      <small class="text-muted"
        >Salário: R$ {{ salario }} | Modalidade: {{ getModalidade }} | Tipo:
        {{ getTipo }} | Publicação: {{ getPublicacao }}</small
      >
    </div>
  </div>
</template>

<script>
export default {
  name: 'VagaComponent',
  //props: ['tituloVagaTeste', 'descricaoVaga', 'salario', 'modalidade', 'tipo', 'publicacao'],
  props: {
    titulo: {
      type: String,
      required: true,
      validator(p) {
        //console.log('Prop: ', p, )
        if (p.length < 6) return false; //se estiver inválido
        return true; //se estiver válido
      },
    },
    descricao: {
      type: String,
      default: 'sem descricao',
    },
    salario: {
      type: [Number, String],
      required: true,
    },
    modalidade: {
      type: String,
      required: true,
    },
    tipo: {
      type: String,
      required: true,
    },
    publicacao: {
      type: String,
      required: true,
    },
  },
  computed: {
    getModalidade() {
      const modalidade = { 1: 'Home Office', 2: 'Presencial' };
      return modalidade[this.modalidade];
    },
    getTipo() {
      const tipo = { 1: 'CLT', 2: 'PJ' };
      return tipo[this.tipo];
    },
    getPublicacao() {
      return new Date(this.publicacao).toLocaleDateString();
    },
  },
};
</script>

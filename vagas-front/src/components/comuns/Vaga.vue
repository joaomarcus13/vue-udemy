<template>
  <div class="card">
    <div class="card-header bg-dark text-white">{{ titulo }}</div>
    <div class="card-body">
      <p>{{ descricao }}</p>
    </div>
    <div class="card-footer">
      <small class="text-muted"
        >Salario: R$ {{ salario }} | Modalidade: {{ modalidade }} | Tipo: {{ tipo }} | Publicacao:
        {{ new Date(publicacao).toLocaleDateString() }}</small
      >
    </div>
  </div>
</template>

<script>
export default {
  name: 'BaseVaga',
  props: {
    titulo: String,
    descricao: String,
    salario: Number,
    modalidade: String,
    tipo: String,
    publicacao: String,
  },
};
</script>

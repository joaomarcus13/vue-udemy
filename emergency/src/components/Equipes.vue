<template>
  <div>
    <div class="row">
      <div class="col">
        <h5><i class="bi-clipboard-check me-2"></i>Equipes montadas</h5>
      </div>
    </div>
    <div class="row">
      <div class="col">
        <ListaItens tipo="equipes-montadas" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import ListaItens from '@/components/ListaItens.vue';

export default {
  name: 'EquipesComponent',
  components: {
    ListaItens,
  },
};
</script>

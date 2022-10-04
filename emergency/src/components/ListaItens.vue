<template>
  <div>
    Lista Itens {{ tipo }}
    <br />
    <item />
  </div>
</template>

<script lang="ts">
import Item from '@/components/Item.vue';

export default {
  name: 'ListaItens',
  components: {
    Item,
  },
  props: {
    tipo: String,
  },
};
</script>

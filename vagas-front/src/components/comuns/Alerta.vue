<template>
  <div>
    <div :class="`alert ${status} alerta`" role="alert">
      <slot name="titulo">
        <h5>titulo padrao</h5>
      </slot>
      <hr />
      <slot name="descricao">
        <p>Descricao padrao</p>
      </slot>
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'AlertaComponent',
  props: {
    status: String,
  },
};
</script>

<style scoped>
.alerta {
  position: absolute;
  right: 0;
}
</style>

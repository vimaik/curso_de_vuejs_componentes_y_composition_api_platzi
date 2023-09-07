<template>
  <div>
    <button @click="toggle">Modal</button>
    <div v-show="show" class="modal">
      <h1>Título</h1>
      <p>Texto informativo del modal</p>
      <button @click="toggle">Cerrar</button>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      show: false,
    };
  },
  methods: {
    toggle() {
      this.show = !this.show;
    },
  },
};
</script>
<style></style>

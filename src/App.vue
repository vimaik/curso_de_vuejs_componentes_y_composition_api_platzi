<template>
  <button @click="show = !show">Menú</button>
  <transition name="fade">
    <Menu v-show="show" />
  </transition>
</template>

<script>
import Menu from "./components/Menu.vue";
export default {
  name: "App",
  components: {
    Menu,
  },
  data() {
    return {
      show: false,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}
.fade-leave-active,
.fade-enter-active {
  transition: opacity 0.5s ease;
}
/* 
OPCIONES DEL EJEMPLO DE EFECTO DE TRANSISICÓN 'fade'

fade-enter-from
fade-enter-active
fade-enter-to
fade-leave-from
fade-leave-active
fade-leave-to

dónde,
  'fade' correspondeal efecto de transición a aplicar
  'enter' corresponde al elemento entrante cuando dse activa ese efecto de transición
  'leave' corresponde al elemento saliente cuando dse activa ese efecto de transición
  'from' corresponde al momento en el que se inicia el efecto de transición
  'active' corresponde al momento durante el cual la transición está activa
  'to' corresponde al momento en el que la transición ha acabado
*/
</style>

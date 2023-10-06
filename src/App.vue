<template>
  <Home
    first-name="Víctor"
    last-name="Muñoz García"
    unexpected-attr="valor1"
  ></Home>
</template>

<script>
import Home from "@/components/Home.vue";
import { provide } from "vue";

export default {
  name: "App",
  components: {
    Home,
  },
  setup() {
    // El segundo parámetro de 'provide' puede ser una constante, como aquí, o una variable
    // reactiva definida mediante 'ref' o 'toRefs', por ejemplo
    provide("username", "victor.munoz");
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
</style>

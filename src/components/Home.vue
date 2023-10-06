<template>
  <div>Full Name: {{ fullName }}</div>
  <div>Username: {{ userName }}</div>
</template>

<script>
import { toRefs, computed, inject } from "vue";

export default {
  props: {
    firstName: {
      type: String,
      required: false,
      default: "Antonio",
    },
    lastName: {
      type: String,
      required: false,
      default: "Hernández",
    },
  },
  // context contiene atributos: attrs, emit, expose y slots
  // Se puede acceder a uno o varios de ellos mediante la deconstrucción de EMAScript
  setup(props, { attrs, expose }) {
    const { firstName, lastName } = toRefs(props);

    const fullName = computed(() => {
      return `${firstName.value} ${lastName.value}`;
    });

    // La función 'inject' devuelve un valor NO REACTIVO. Para convertirlo en uno
    // deberías utilizar 'toRefs'
    const userName = inject("username");

    console.log(attrs);

    // Para exponer atributos y funciones internos del componentes a otros componentes
    expose({
      fullName,
    });

    return {
      fullName,
      userName,
    };
  },
};
</script>

<template>
  <div>{{ texto1 }}</div>
  <div>Contador en variable de tipo 'primitivo': {{ contador1 }}</div>
  <div>Contador en variable de tipo 'objeto': {{ contador2.counter }}</div>
  <div>{{ texto2 }}</div>
</template>

<script>
// ref >> Para definir variables reactivas de tipo primitivo, en Composition API, o sea, dentro de setup() {}' (CON uso de '.value')
// reactive >> Para definir variables rectivascde tipo objeto, en Composition API, o sea, dentro de 'setup() {}'' (SIN uso de '.value')
import { ref, reactive } from "vue";

export default {
  setup() {
    // Para variables primitivas se usa 'ref' y para asignarles un valor se utiliza '.value'
    const counter = ref(0); // Variable primitiva de tipo numérico, inicializada por defecto
    const texto1 = ref("Hola vue"); // Variable primitiva de tipo string, inicializada por defecto

    const texto2 = ref(); // Variable primitiva sin tipo definido, este se definirá cuando se le asigne un valor mediante '.value'
    texto2.value = "Adios Vue"; // Se define el tipo y el valor de la variable como string y 'Adios Vue' respectivamente

    // Para variables de tipo objeto se usa 'reactive' y no se utiliza '.value' para asignar valor a sus atributos
    const obj = reactive({ counter: 0 });

    // Dentro de 'setup() {}, o lo que es lo mismo, Composition API, se puede usar vanilla JS
    // para manipular las variables'
    setInterval(() => counter.value++, 1000);
    setInterval(() => obj.counter++, 500);

    // Para que estas variables reactivas del Composition API esten disponibles en el componente, se deben especificar en la funcion 'return {}'
    return {
      texto1,
      texto2,
      contador1: counter,
      contador2: obj,
    };
  },
};
</script>

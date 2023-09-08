<template>
  <div>{{ texto1 }}</div>
  <div>Contador en variable de tipo 'primitivo': {{ contador1 }}</div>
  <div>Contador en variable de tipo 'objeto': {{ contador2.counter }}</div>
  <div>{{ texto2 }}</div>
</template>

<script>
// ref >> Para definir variables reactivas de tipo primitivo, en Composition API, o sea, dentro de setup() {}' (CON uso de '.value')
// reactive >> Para definir variables rectivascde tipo objeto, en Composition API, o sea, dentro de 'setup() {}'' (SIN uso de '.value')
import { ref, reactive, watch } from "vue";

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

    // watch' Recibe 2 parámetros: Primero la variable que quieres escuchar y segundo la función que se va a ejecutar cada vez que haya un cambio en el valor de la variable escuchada
    // IMPORTANTE: Con 'reactive' la variable se pasa como return de una función, para eliminar el proxy que el Composition API de VueJS añade en la reactividad de objetos
    watch(
      () => obj.counter,
      (valorActual, valorAnterior) => {
        console.log("reactive: ", valorActual, valorAnterior);
      }
    );

    // IMPORTANTE: Con 'ref' la variable se pasa tal cual ya que el Composition API de VueJS no añade ningún proxy en la reactividad de objetos
    watch(counter, (valorActual, valorAnterior) => {
      console.log("ref: ", valorActual, valorAnterior);
    });

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

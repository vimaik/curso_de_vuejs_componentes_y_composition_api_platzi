<template>
  <div>Full Name: {{ fullName }}</div>
</template>

<script>
import { toRefs, computed } from "vue";

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
  setup(props) {
    const { firstName, lastName } = toRefs(props);

    const fullName = computed(() => {
      return `${firstName.value} ${lastName.value}`;
    });

    return {
      fullName,
    };
  },
};
</script>

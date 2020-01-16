<template>
  <h2>{{ tituloMayus() }}</h2>
</template>

<script>
export default {
  props: {
    titulo: {
      required: true,
      type: String,
      default: "Bien o que so"
    }
  },
  methods: {
    tituloMayus() {
      return this.titulo.toUpperCase();
    }
  }
};
</script>

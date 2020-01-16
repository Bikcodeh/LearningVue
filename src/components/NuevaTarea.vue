<template>
  <div class="input-group">
    <input
      class="form-control mr-1"
      type="text"
      placeholder="Nueva tarea"
      v-model="nuevaTarea"
      v-on:keyup="validarInput"
      @keyup.enter="agregarTarea"
    />
    <span class="input-group-btn">
      <a
        href="#"
        class="btn btn-primary"
        :class="{ disabled: !fillInput }"
        @click="agregarTarea"
        tabindex="-1"
        role="button"
        aria-disabled="true"
        >Agregar tarea</a
      >
    </span>
  </div>
</template>
<script>
export default {
  data: function() {
    return {
      nuevaTarea: "",
      fillInput: false
    };
  },
  props: ["tareas"],
  methods: {
    agregarTarea: function() {
      this.tareas.push({
        texto: this.nuevaTarea,
        terminada: false
      });
      this.$emit("incrementarNumTareas", 1);
      this.nuevaTarea = "";
      this.fillInput = false;
    },
    validarInput: function() {
      if (this.nuevaTarea.trim().length > 0) this.fillInput = true;
      else this.fillInput = false;
    }
  }
};
</script>

<template>
  <div>
    <label for="nombre">Nombre:</label>
    <input v-model="nombre" name="nombre" @input="validateNombre" />
    <span>{{ error }}</span>
  </div>
</template>

<script>
export default {
  props: {
    value: String,
  },
  data() {
    return {
      nombre: this.value || '',
      error: '',
    };
  },
  methods: {
    validateNombre() {
      this.error = '';

      if (this.nombre.length < 5 || this.nombre.length > 18) {
        this.error = 'El nombre debe tener entre 5 y 18 caracteres.';
      }

      this.$emit('update:nombre', this.error === '' ? this.nombre : '');
    },
  },
};
</script>




<template>
  <div></div>
</template>

<script lang="ts" setup></script>

<style scoped></style>
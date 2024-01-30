<template>
  <div>
    <label for="apellido">Apellido:</label>
    <input v-model="apellido" name="apellido" @input="validateApellido" />
    <span>{{ error }}</span>
  </div>
</template>

<script>
export default {
  props: {
    nombre: String,
    value: String,
  },
  data() {
    return {
      apellido: this.value || '',
      error: '',
    };
  },
  methods: {
    validateApellido() {
      this.error = '';

      if (this.apellido === this.nombre) {
        this.error = 'El apellido no puede ser igual al nombre.';
      }

      this.$emit('update:apellido', this.error === '' ? this.apellido : '');
    },
  },
};
</script>

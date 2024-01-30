<template>
  <div>
    <label for="edad">Edad:</label>
    <input type="number" v-model="edad" name="edad" @input="validateEdad" />
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
      edad: this.value || '',
      error: '',
    };
  },
  methods: {
    validateEdad() {
      this.error = '';

      const edadNumerica = Number(this.edad);

      if (isNaN(edadNumerica) || edadNumerica <= 0 || edadNumerica >= 60) {
        this.error = 'La edad debe ser un número mayor que 0 y menor que 60.';
      }

      this.$emit('update:edad', this.error === '' ? this.edad : '');
    },
  },
};
</script>

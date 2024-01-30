<template>
  <div>
    <label for="genero">Género:</label>
    <select v-model="selectedGenero" name="genero" @change="validateGenero">
      <option value="masculino">Masculino</option>
      <option value="femenino">Femenino</option>
      <option value="otro">Otro</option>
    </select>

    <!-- Mostrar el campo de texto solo si se selecciona "Otro" -->
    <input v-if="selectedGenero === 'otro'" v-model="otroGenero" name="otroGenero" placeholder="Especificar género" @input="validateGenero" />

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
      selectedGenero: this.value || 'masculino',
      otroGenero: '',
      error: '',
    };
  },
  methods: {
    validateGenero() {
      this.error = '';

      if (this.selectedGenero === 'otro' && !this.otroGenero.trim()) {
        this.error = 'Por favor, especifica tu género.';
      }

      this.$emit('update:genero', this.error === '' ? this.otroGenero || this.selectedGenero : '');
    },
  },
};
</script>

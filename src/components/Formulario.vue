<!-- Formulario.vue -->
<template>
  <div class="form">
    <h1>Formulario</h1>

    <NombreComponent v-model="nombre" @update:nombre="updateNombre" />

    <ApellidoComponent :nombre="nombre" v-model="apellido" @update:apellido="updateApellido" />

    <EdadComponent v-model="edad" @update:edad="updateEdad" />

    <GeneroComponent v-model="genero" @update:genero="updateGenero" />

    <form @submit.prevent="sendForm">
      <input type="submit" value="Enviar">
    </form>

    <!-- Mostrar los datos proporcionados -->
    <div v-if="datosEnviados">
      <h2>Datos proporcionados:</h2>
      <p><strong>Nombre:</strong> {{ nombre }}</p>
      <p><strong>Apellido:</strong> {{ apellido }}</p>
      <p><strong>Edad:</strong> {{ edad }}</p>
      <p><strong>Género:</strong> {{ genero }}</p>
    </div>

    <!-- Botón para limpiar los datos -->
    <button @click="limpiarFormulario">Limpiar</button>
  </div>
</template>

<script>
import NombreComponent from './NombreComponent.vue';
import ApellidoComponent from './ApellidoComponent.vue';
import EdadComponent from './EdadComponent.vue';
import GeneroComponent from './GeneroComponent.vue';

export default {
  components: {
    NombreComponent,
    ApellidoComponent,
    EdadComponent,
    GeneroComponent,
  },
  data() {
    return {
      nombre: '',
      apellido: '',
      edad: '',
      genero: '',
      datosEnviados: false,
    };
  },
  methods: {
    sendForm() {
      // Realizar validaciones aquí si es necesario
      console.log('Nombre enviado:', this.nombre);
      console.log('Apellido enviado:', this.apellido);
      console.log('Edad enviada:', this.edad);
      console.log('Género enviado:', this.genero);

      this.datosEnviados = true;
    },
    updateNombre(value) {
      this.nombre = value;
    },
    updateApellido(value) {
      this.apellido = value;
    },
    updateEdad(value) {
      this.edad = value;
    },
    updateGenero(value) {
      this.genero = value;
    },
    limpiarFormulario() {
      // Limpiar los datos del formulario
      this.nombre = '';
      this.apellido = '';
      this.edad = '';
      this.genero = '';
      this.datosEnviados = false;
    },
  },
};
</script>

<style scoped>
  .form {
    max-width: 400px;
    margin: 0 auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    background-color: none;
  }

  h1 {
    text-align: center;
    color: #333;
  }

  form {
    margin-top: 20px;
  }

  label {
    display: block;
    margin-bottom: 8px;
    color: #333;
  }

  input,
  select {
    width: 100%;
    padding: 8px;
    margin-bottom: 16px;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-sizing: border-box;
  }

  input[type="submit"],
  button {
    background-color: #4caf50;
    color: white;
    padding: 10px 15px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }

  input[type="submit"]:hover,
  button:hover {
    background-color: #45a049;
  }

  .datos-enviados {
    margin-top: 20px;
    padding: 10px;
    border: 1px solid #4caf50;
    border-radius: 4px;
    background-color: #dff0d8;
  }

  .datos-enviados h2 {
    color: #4caf50;
  }

  .limpiar-button {
    background-color: #f44336;
    color: white;
    padding: 10px 15px;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }

  .limpiar-button:hover {
    background-color: #d32f2f;
  }
</style>

<template>
  <div id="app">
    <h1>App (Actual {{ preguntaActual + 1 }})</h1>
    <Card
      v-for="pregunta in preguntas"
      :key="pregunta.numero"
      :pregunta="pregunta"
      :activa="preguntaActual"
      @onRespuesta="irASiguiente"
    />
    <button type="button" @click="reiniciar">Reiniciar</button>
  </div>
</template>

<script>
import Card from './components/Card.vue';

export default {
  name: 'App',
  components: {Card},
  data() {
    return {
      preguntaActual: 1,
      preguntas: [
        {
          numero: 1,
          titulo: 'titulo 1',
          respuesta: 'A',
          activa: false,
          respondida: false,
        },
        {
          numero: 2,
          titulo: 'titulo 2',
          respuesta: 'B',
          activa: false,
          respondida: false,
        },
        {
          numero: 3,
          titulo: 'titulo 3',
          respuesta: 'B',
          activa: false,
          respondida: false,
        },
        {
          numero: 4,
          titulo: 'titulo 4',
          respuesta: 'B',
          activa: false,
          respondida: false,
        },
      ],
    };
  },
  methods: {
    irASiguiente() {
      if (this.preguntaActual > this.preguntas.length) {
        this.preguntaActual = this.preguntas.length;
      }
      if (this.preguntaActual === this.preguntas.length) {
        alert("Bien! terminaste");
      }
      this.preguntaActual++;
    },
    reiniciar() {
      this.preguntaActual = 1;
    }
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

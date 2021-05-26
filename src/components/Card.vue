<template>
  <div id="card">
    <h1>{{ pregunta.numero }}. {{ pregunta.titulo }}</h1>
    <input
      type="text"
      value=""
      v-model="respuesta"
      :disabled="activa != pregunta.numero"
      @change="limpiar"
    />
    <br />
    <input
      type="submit"
      value="save"
      :disabled="activa != pregunta.numero"
      @click="save"
    />
    <p v-if="pregunta.respondida && respuesta === pregunta.respuesta">
      Es correcto!
    </p>
    <p v-if="pregunta.respondida && respuesta != pregunta.respuesta">
      Es in-correcto!
    </p>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    pregunta: Object,
    activa: Number,
  },
  data() {
    return {
      respuesta: null,
    };
  },
  components: {},
  methods: {
    save() {
      alert('saving ' + this.pregunta.titulo);
      this.pregunta.respondida = true;
      this.$emit('onRespuesta');
    },
    limpiar() {
      this.pregunta.respondida = false;
    },
  },
};
</script>

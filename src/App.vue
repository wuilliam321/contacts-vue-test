<template>
  <div id="app">
    <form @submit="guardar">
      <label for="name">
        Nombre:
        <input id="name" name="name" />
      </label>
      <input type="submit" value="Guardar" />
    </form>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'App',
  components: {},
  methods: {
    async guardar(event) {
      console.log(event);
      event.preventDefault();
      alert('vamos a guardar');
      const data = {
        nombre: 'Carlos',
      };
      const res = await axios.post('http://127.0.0.1:5000/contactos', data);
      alert(JSON.stringify(res.data));
    },
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

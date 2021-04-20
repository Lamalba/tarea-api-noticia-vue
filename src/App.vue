<template>
<div>
  <Noticia />
</div>
</template>

<script>
import Noticia from "./components/Noticia.vue";
export default {
  name: "App",
  components: {
    Noticia,
  },
};
</script>

<style>
#app {
  font-family: Roboto, Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>


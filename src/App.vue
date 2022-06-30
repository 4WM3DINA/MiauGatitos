<template>
  <div id="app">
    <img alt="Cat" src="./assets/cats-cat-wallpaper-preview.jpg" />
    <hr />
    <ComponenteGatitos />
  </div>
</template>

<script>
import ComponenteGatitos from "./components/ComponenteGatitos";

export default {
  name: "App",
  components: {
    ComponenteGatitos,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #050505;
  font-weight: bold;
  font-size: 1.5rem;
  background-image: url("https://img.wallpapersafari.com/desktop/1600/900/98/67/9b3Pr6.jpg");
  background-size: cover;
  background-repeat: no-repeat;
}
</style>

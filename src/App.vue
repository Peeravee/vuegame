<template>
  <div id="app">
    <br />
    <img class="rounded-circle" src="https://cdn.freebiesupply.com/logos/thumbs/2x/fighter-logo.png" width="20%" />
    <HelloWorld msg = "STREET FIGHTERS" />
    <br />
    
    <div>
      <botton />
    </div>
  </div>
</template>
<script>
import HelloWorld from "./components/HelloWorld.vue";
import botton from "./components/botton.vue";
export default {
  name: "App",
  components: {
    HelloWorld,
    botton,
  },
};
</script>

<style>
#app {
  background-image: url(https://cdn.wallpapersafari.com/58/11/DfTK7O.gif);
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  position: relative;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color:azure;
}
</style>

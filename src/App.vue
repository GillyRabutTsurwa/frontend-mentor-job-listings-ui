<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
    <Banner
      v-for="currentItem in items"
      v-bind:key="currentItem.id"
      v-bind:itemsProp="currentItem"
    />
  </div>
</template>

<script>
import jsonData from "./data.json";
import Banner from "./components/Banner";

export default {
  name: "App",
  data() {
    return {
      items: jsonData
    };
  },
  components: {
    Banner: Banner
  },
  async created() {
    console.log("App rendering...");
  }
};
</script>

<style lang="scss">
@import "./App.css";
#app {
  width: 75%;
  height: 100%;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 3rem auto;
}
</style>

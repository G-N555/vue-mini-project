<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <h1>{{ title }}</h1>
    <navbar />
    <allphotos />
    <singlePhoto v-on:click="changeView"/>
  </div>
</template>

<script>
import Navbar from "./components/Navbar";
import AllPhotos from "./components/AllPhotos"
// import SinglePhoto from "./components/SinglePhoto"
export default {
  name: "App",
  components: {
    navbar: Navbar,
    allphotos: AllPhotos,
    // singlePhoto: SinglePhoto
  },
  data: () => ({
    title: "Yes, photo is here"
  })
};
</script>

<style>
#app {
  text-align: center;
  background-color: rgb(7, 2, 27);
}
</style>

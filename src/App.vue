<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <h1>{{ title }}</h1>
    <navbar />
    <allphotos @changeView="onChangeView"/>
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
  },
  data: () => ({
    title: "Yes, photos are here",
    photos: "",
  }),
  methods: {
    onChangeView: (event) => {
      this.photos = event;
    }
  }
};
</script>

<style>
#app {
  text-align: center;
  background-color: rgb(7, 2, 27);
  color: white;
}
</style>

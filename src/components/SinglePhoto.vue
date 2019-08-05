<template>
  <img id="singlePhoto" v-on:click="showAll" :src="'data:image/png;base64,' + photo">
</template>

<script>
import Allphotos from "../components/AllPhotos"
export default {
  name: "SinglePhoto",
};
</script>

<style></style>

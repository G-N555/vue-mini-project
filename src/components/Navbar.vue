<template>
<div>
  <button v-on:click="refresh">Fresh</button>
  <upload class="input">UPLOAD</upload>
</div>
</template>

<script>
import Upload from "./Upload"
export default {
  name: "Navbar",
  components: {
    upload: Upload
  },
  methods: {
    refresh: function(e) {
      e.preventDefault();
      window.location.reload();
    }
  }

};
</script>

<style>
</style>

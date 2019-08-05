<template>
<div>
  <button v-on:click="refresh">Fresh</button>
  <button>Home</button>
  <upload>upload</upload>
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

<style></style>

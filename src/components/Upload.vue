<template>
  <input type="file" id="upload" v-on:change="uploadFile($event)"/>
</template>

<script>
//with curly brace, this is deconstruction which grabed value,
//if without curly brace, it is just called object and does not work as function.
import { saveObject } from "../../utils/index"
export default {
  name: "Upload",
  methods:{
    uploadFile: function(e){
      saveObject(e.target.files[0]);
    }
  }
};
</script>

<style></style>

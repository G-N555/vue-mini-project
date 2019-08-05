<template>
  <div id="allphotos" class="photo-container">
     <img class="photos" :id="index" v-on:click="$emit('changeView')" v-for="(item,index) in photos" :src="'data:image/png;base64,' + item" :key="index"/>
  </div>
</template>

<script>
import { listObjects, getSingleObject } from "../../utils/index"
export default {
  name: "AllPhotos",
  data: () => ({
    photos: [],
    currentStatus: true,
  }),
  created: function() {
    listObjects().then((list) =>{
      list.map(data =>{
        getSingleObject(data.Key).then((photoData) =>{
          this.photos.push(photoData)
        }
        );
      })
    })
  },
  methods: {
    changeView: function(e){
      this.photos = this.photos[e.target.id];
    }
  }
};
</script>

<style>
#allphotos{
  -webkit-column-count: 4;
     -moz-column-count: 4;
          column-count: 4;
}
.photos{
  border: solid 1px rgb(4, 4, 53);
  height: 70px;
  width: 70px;
  border-radius: 5% 5%;
  cursor: pointer;
}
.photos:hover {
  -webkit-transform: rotate(360deg);
          transform: rotate(360deg);
}
</style>

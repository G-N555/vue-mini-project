<template>
<!--
  for selectPhoto, I made 2 image tags and made condition each block to change view.
  Then, I made another data that is "selectedPhoto" to store single photodata to apply single image tag.
  !-->
  <div id="allphotos" class="photo-container" v-if="currentStatus===true">
     <img class="photos" :id="index" v-on:click="changeView" v-for="(item,index) in photos" :src="'data:image/png;base64,' + item" :key="index"/>
  </div>
  <div id="singlePhoto" class="single-photo-container" v-else>
     <img class="single" v-on:click="changeView" :src="'data:image/png;base64,' + selectedPhoto"/>
  </div>
</template>

<script>
import { listObjects, getSingleObject } from "../../utils/index"
export default {
  name: "AllPhotos",
  data: () => ({
    photos: [],
    currentStatus: true,
    selectedPhoto: "",
  }),
  created: function() {
    listObjects().then((list) =>{
      list.slice(0,100).map(data =>{
        getSingleObject(data.Key).then((photoData) =>{
          this.photos.push(photoData)
        }
        );
      })
    })
  },
  methods: {
    changeView(e) {
      if(this.currentStatus){
        this.selectedPhoto = this.photos[e.target.id];
        this.currentStatus = !this.currentStatus
      } else {
        this.currentStatus = !this.currentStatus;
      }
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
.single-photo-container{
  display: block;
  height: auto;
  max-width: 80%;
  margin: 0 auto;
}
.single {
  height:auto;
  max-width: 100%;
  border-radius: 5% 5%;
  border: dashed 5px;
  cursor: pointer;
}
</style>

<template>
  <div id="app">
    <img src="./assets/img/logo.png">
    <h1>{{ jsonData.title }}</h1>
    <h2>{{ jsonData.description }}</h2>
    <gallery v-bind:title="jsonData.top_gallery_title" v-bind:items="jsonData.top_gallery_items" @THUMB_CLICK="onThumbClick"></gallery>
    <manifest v-bind:manifest="jsonData.manifest"></manifest>
    <gallery v-bind:title="jsonData.bottom_gallery_title" v-bind:items="jsonData.bottom_gallery_items" @THUMB_CLICK="onThumbClick"></gallery>
    <fullImage v-if="showFullImage" v-bind:imageUrl=fullImageUrl @BUTTON_CLOSE_CLICK="closeFullImage"></fullImage>
  </div>
</template>

<script>
import axios from 'axios'
import gallery from './components/gallery.vue';
import manifest from './components/manifest.vue';
import fullImage from './components/fullImage.vue';

export default {
  components:{
      gallery, 
      manifest,
      fullImage  
    },
  name: 'app',
  data () {
    return {
      jsonData: {},
      showFullImage: false,
      fullImageUrl:null
    }
  },
  mounted () {
    axios
      .get('./src/assets/json/data-it.json')
      .then(response => {
        this.jsonData = response.data;
        // console.log(this.jsonData);
      });
  },

  methods:{
    onThumbClick:function(payload)
    {
      this.showFullImage=true;
      this.fullImageUrl=payload;
    },

    closeFullImage:function()
    {
      this.showFullImage=false;
    }
  }
}


</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>

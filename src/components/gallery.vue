<template>
    <div class="gallery">
        <h2 class="center">{{title}}</h2>
        <div class="item" v-for="(item, i) in items" :key="i">
            <img class="inline" v-bind:src="items[i].thumb"  @click="openImage(i)">
        </div>
    </div>

</template>

<script>
import fullImage from './fullImage.vue';

export default {

    props:["title", "items"],

    data: function() {
        return {
            
        }
    },

    methods: {
        openImage: function(id){
            var imageUrl=this.items[id].full;
            
            this.$emit("THUMB_CLICK",imageUrl);
        }
        
    }

}
</script>

<style scoped>
    .gallery{
        display: block;
        margin: 0;
        height: auto;
        background-color: grey;
        position: relative;
        text-align: left;
    }

    .center {
        text-align: center
    }

    .item {
        width: 25%;
        height: auto;
        display: inline-block;
        vertical-align: top;
    }

    .inline {
        width: 100%;
        height: auto;
    }
</style>

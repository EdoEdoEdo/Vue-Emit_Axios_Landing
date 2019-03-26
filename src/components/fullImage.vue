<template>
    <div class="full" @click="close">
        <h1>{{imageUrl}}</h1>
    </div>
</template>

<script>

export default {
     data: function() {
        return {
            
        }
    },

    props:["imageUrl"],

    methods: {
        
        close: function()
        {
            this.$emit("BUTTON_CLOSE_CLICK");
        }
    }
}

</script>

<style scoped>

.full {
    height: 100%;
    width: 100%;
    top: 0;
    left: 0;
    display: block;
    position: fixed;
    background: red;
    opacity: 0.4;
    z-index: 99;
}

</style>


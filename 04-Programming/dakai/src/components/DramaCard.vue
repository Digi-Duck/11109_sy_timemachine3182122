<template>
    <div>
        <img :src="img1" alt="">
    </div>
</template>

<style scoped lang="scss">
</style>

<script>
    // load every picture files in context. 
    const context = require.context("../assets/", false, /\.(png|jpg|gif|jpeg|webp|ico)$/);
    //let context turn into routes
    const images = context.keys().map(context);

    export default{
        data(){
            return{
                images: images,
                img1: images[1],
            }
        },
        mounted() {
        },
        methods:{
        }
    }
</script>
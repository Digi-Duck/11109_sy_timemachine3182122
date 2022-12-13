<template>
    <div class="card-banner">
        <div v-for="( pic , index ) in images" :key="index">
            <div class="card" :style="{backgroundImage: 'url(' + pic + ')'}"></div>
        </div>
    </div>
</template>

<style scoped lang="scss">
.card-banner{
    width: calc( 100vw - 20px);
    height: auto;
    margin: 0px;
    padding: 0px;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    flex-wrap: wrap;
}
.card-banner>div{
    width: calc( 50% - 5px);
    height: auto;
    margin: 0px 0px 10px;
}
.card{
    width: 100%;
    height: 450px;
    background-position: center center;
    background-repeat: no-repeat;
    background-size: cover;
}
@media(min-width:1920px){

}
@media(min-width:1280px){
    .card-banner>div{
    width: calc( 33% - 5px);
    height: auto;
    margin: 0px 0px 10px;
}
}
@media(min-width:768px){
  
}
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
            }
        },
        mounted() {
        },
        methods:{
        }
    }
</script>
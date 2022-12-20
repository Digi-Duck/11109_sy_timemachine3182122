<template>
    <swiper
        class="card-banner"
        :slides-per-view="2"
        :space-between="50"
        :loop="true"
        @swiper="onSwiper"
        @slideChange="onSlideChange"
    >
        <swiper-slide v-for="( pic , index ) in images" :key="index">
            <div class="card" :style="{backgroundImage: 'url(' + pic + ')'}"></div>
            <p>{{fileName[index]}}</p>
        </swiper-slide>
    </swiper>
</template>>

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
    background-color: #eedcdb;
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
    transition-duration: 0.5s;
}
.smaller{
    scale: 0.5 0.5 ;
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
// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from 'swiper/vue';

// Import Swiper styles
import 'swiper/css';
// load every picture files in context. 
const context = require.context("../assets/Goods/", false, /\.(png|jpg|gif|jpeg|webp|ico)$/);
const fileName = context.keys();
//let context turn into routes
const images = context.keys().map(context);

export default{
    components: {
      Swiper,
      SwiperSlide,
    },
    setup() {
      const onSwiper = (swiper) => {
        console.log(swiper);
      };
      const onSlideChange = () => {
        console.log('slide change');
      };
      return {
        onSwiper,
        onSlideChange,
      };
    },
    data(){
        return{
            images: images,
            fileName: fileName,
        }
    },
    mounted() {
        const cards = document.querySelectorAll('.card');
        
        cards.forEach((card)=>{
            card.addEventListener('click',()=>{
                card.classList.toggle("smaller");
            });
        });
    },
    methods:{
    }
}
</script>
<template>
  <div class="cover">
    <div class="guitar-background">
      <div class="guitar">
        <img :src="guitar" alt="">
      </div>
    </div>
    <div class="outside">
      <div class="door-background">
        <div class="door">
          <div class="store" :style="{backgroundImage:'url(' + store + ')'}">
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped >
.cover {
  width: 100vw;
  height: auto;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: center;
  position: relative;
}

.guitar-background{
  width: 100%;
  height: calc(100vh - 82px);
  background-color: #eedcdb;
}

.guitar {
  width: 100%;
  height: 50vh;
  display: flex;
  flex-direction: row;
  justify-content: center;
}

.guitar>img {
  height: 100%;
  width: auto;
}

.outside{
  width: 100%;
  height: 600vh;
  background-color: #eedcdb;
}
.door-background{
  width: 100%;
  height: 100vh;
  transition: linear;
}

.door {
  position: absolute;
  width: 100%;
  height: auto;
  clip-path: ellipse(25% 75% at 50% 100%);
  scale: 1;
  transition: linear;
  transform-origin: center center;
}
.store{
  width: 100vw;
  height: 100vh;
  left: 0px;
  scale: 1.3;
  background-repeat: no-repeat;
  background-size: contain;
  background-position: center;
}
.fixed{
  z-index: 1;
  position: fixed;
  left: 0%;
  top: 0%;
}
</style>

<script>
import guitar from '@/assets/guitar-hero.png';
import store from '@/assets/store.jpg';

export default {
  data() {
    return {
      guitar: guitar,
      store: store,
    };
  },
  method(){

  },
  mounted(){
    const doorBackground = document.querySelector('.door-background');
    let door = document.querySelector('.door');
    let store = document.querySelector('.store');


    window.addEventListener('scroll', ()=>{
      if ( window.scrollY >= window.innerHeight && window.scrollY < window.innerHeight * 2 ){
        doorBackground.classList.add('fixed');
        
        let scale = window.scrollY / window.innerHeight;
        let width = ((( scale - 1 ) * 50 ) + 50 );

        // door.style.width = width + '%';
        // door.style.marginLeft = (100 - width) / 2 + '%';
        door.style.scale = scale;
        // clip-path: ellipse(25% 75% at 50% 100%);
        door.style.clipPath ='ellipse('+ (width / 2) + '% '+ ( (width/2) + 50 )+ '% at '+ 50 + '% '+ 100 +'%)';
        store.style.scale = (1.3 / ( scale ));
      }
      else if (window.scrollY < window.innerHeight){
        doorBackground.classList.remove('fixed');
        door.style.scale = 1;
        door.style.clipPath = 'ellipse(25% 75% at 50% 100%)';
        store.style.scale = 1.3;
      }
      
    });
  },

}
</script>

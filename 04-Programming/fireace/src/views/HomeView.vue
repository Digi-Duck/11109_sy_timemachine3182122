<template>
  <div class="home">
    <MainEffect/>
    <NavBar/>
  </div>
</template>

<script>
// @ is an alias to /src
import MainEffect from '@/components/MainEffect.vue';
import NavBar from '@/components/NavBar.vue'

export default {
  name: 'MainCompoent',
  components: {
    MainEffect,
    NavBar
  }
}
</script>

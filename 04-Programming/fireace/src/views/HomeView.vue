<template>
  <div class="home">
    <MainComponent/>
  </div>
</template>

<script>
// @ is an alias to /src
import MainComponent from '@/components/MainComponents.vue'

export default {
  name: 'MainCompoent',
  components: {
    MainComponent
  }
}
</script>

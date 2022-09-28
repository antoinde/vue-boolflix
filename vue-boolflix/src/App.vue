// API Key: 5c5ab0c379b45df5bb4161e9bbb65578
// link API momentaneo: https://api.themoviedb.org/3/search/movie?api_key=e99307154c6dfb0b4750f6603256716d&query=ritorno+al+fut
<template>
  <div id="app">
    <div class="container">
      <HeaderComponent />
      <MainComponent />
    </div>
  </div>
</template>

<script>
import HeaderComponent from '@/components/HeaderComponent.vue'
import MainComponent from '@/components/MainComponent.vue'

export default {
  name: 'App',
  components: {
    HeaderComponent,
    MainComponent
  }
}
</script>

<style lang="scss">
@import '@/assets/style/style.scss';

</style>

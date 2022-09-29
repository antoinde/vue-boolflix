<!-- 
  API Key: 5c5ab0c379b45df5bb4161e9bbb65578
link API momentaneo: https://api.themoviedb.org/3/search/movie?api_key=e99307154c6dfb0b4750f6603256716d&query=ritorno+al+fut
-->
<template>
  <div id="app">
    <div class="container">
      <HeaderComponent @search="sendRequest"/>
      <MainComponent :sentFilms="films"/>
    </div>
  </div>
</template>

<script>
import HeaderComponent from '@/components/HeaderComponent.vue'
import MainComponent from '@/components/MainComponent.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    HeaderComponent,
    MainComponent
  },
  data(){
    return {
      myAPI: '5c5ab0c379b45df5bb4161e9bbb65578',
      films: []
    }
  },
  methods: {
    sendRequest(textToSearch){
      console.log("textToSearch (padre): ", textToSearch);

      axios
      .get(`https://api.themoviedb.org/3/search/movie?api_key=${this.myAPI}&language=it_IT&query=${textToSearch}`)
      .then( (response) => {
        console.log(response);

        // se abbiamo ricevuto la risposta correttamente, salviamola
        if(response.status === 200) {
          this.films=response.data.results;
          console.log("Film salvati in locale: ", this.films);
        }
        //se si è verificato un errore nella richiesta allora.. vari casi
        else {
          console.log("Il server non funziona correttamente! status=", response.status);
        }
      });
    }
  }
}
</script>

<style lang="scss">
@import '@/assets/style/style.scss';

</style>

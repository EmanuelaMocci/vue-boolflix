<template>
  <div id="app">
    <!-- 4) Ora passo l'evento del figlio tramite $emit (search), quindi il nome dell'evento, searchMovie è il metodo 
    non appne avie scatenato l'evento, rinago in ascolto del metodo searchMovie-->
    <Header @search="searchMovie"/>
    <Films :films="films"/>
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Films from './components/Films.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    Films
  },
  data(){
    return{
      // 5) Creo un array vuoto dove salvare i dati
      films: []
    }
  },
  methods: {
    // 3) Richiamo la funzione con un paramentro search (può essere chiamato come si vuole)
    searchMovie(search){
      // Facciamo partire la chiamata qui perchè avviene dopo aver cliccato l'evento
      axios.get('https://api.themoviedb.org/3/search/movie?api_key=e99307154c6dfb0b4750f6603256716d&query=ritorno+al+fut uro', {
        params: {
          api_key: 'e99307154c6dfb0b4750f6603256716d',
          query: search,
          language: 'it-IT'
      }
    })
    .then((response) => {
      // 6) Salvare i dati results in movieSearched
      this.films = response.data.results;
    });
    }
  }
    }
  
</script>

<style lang="scss">

</style>

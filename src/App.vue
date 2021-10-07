<template>
  <div id="app">
    <!-- 4) Ora passo l'evento del figlio tramite $emit (search), quindi il nome dell'evento, searchMovie è il metodo 
    non appena viene scatenato l'evento, rimango in ascolto del metodo searchMovie-->
    <Header @search="searchMovie"/>
    <Films :films="films" :series="series"/>
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
      films: [],
      series: []
    }
  },
  methods: {
    // 3) Richiamo la funzione con un paramentro search (può essere chiamato come si vuole)
    searchMovie(search){
      // Facciamo partire la chiamata qui perchè avviene dopo aver cliccato l'evento
      axios.get('https://api.themoviedb.org/3/search/movie', {
        params: {
          api_key: 'aad62cbe2fe92d75516ca3bc33211c38',
          query: search,
          language: 'it-IT'
        }
      })
      .then((response) => {
        // 6) Salvo i dati results in films
        this.films = response.data.results;
      });

      // Effettuo una nuova chiamata all'interno della funzione searchMovie per le serie tv
      axios.get('https://api.themoviedb.org/3/search/tv', {
        params: {
          api_key: 'aad62cbe2fe92d75516ca3bc33211c38',
          query: search,
          language: 'it-IT'
        }
      })
      .then((response) => {
        // 6) Salvo i dati results in series
        this.series = response.data.results;
      });
    }
  }
}
  
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@100;200;300;400;500&display=swap');
@import '~@fortawesome/fontawesome-free/css/all.css';
</style>

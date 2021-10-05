<template>
  <div id="app">
    <Header/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header
  },
  data(){
        return{
            movies: []
        }
    },
  created(){
    axios.get('https://api.themoviedb.org/3/search/movie', {
    params: {
      api_key: 'aad62cbe2fe92d75516ca3bc33211c38',
      query: 'ritorno+al+futuro',
      language: 'it-IT'
    }
    })
    .then(function (response) {
      console.log(response.data.results);
    }); 
      // axios
      // .get("https://api.themoviedb.org/3/search/movie?api_key=e99307154c6dfb0b4750f6603256716d&query=ritorno+al+fut")
      // .then((res) => {
      //     this.movies = res.data.response;
      // });
  }
}
</script>

<style lang="scss">

</style>

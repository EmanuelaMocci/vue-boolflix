<template>
    <div class="movies-container">
        <div class="trailer">
            <section>
                <iframe width="560" height="315" src="https://www.youtube.com/embed/Ne9wFo2aq3U" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; allow='autoplay'; picture-in-picture" allowfullscreen></iframe>
                <div class="dettagli-video">
                    <img src="https://occ-0-2908-2774.1.nflxso.net/dnm/api/v6/tx1O544a9T7n8Z_G12qaboulQQE/AAAABbDPbGOaZ2jDzuKx0Qqz4AkcP6LopQGYezdUkfKGMXLtiOIiVdNvxH1oPi0GyWjpti0wySwGT6wQSTXe4mA04YwzGeI-vEZjBaFRG2ipM0EWZ7XI8ZyvpUfT2JnX4tYlpdgxkxZEfaLue_N3_Xlj9lDUWGtP4QuQW7os9jyaC7b5.webp?r=695" alt="">
                    <div class="trama">In 1990s Berlin, an artist and a hacker invented a new way to see the world. Years later, they reunite to sue Google for patent infringement on it.</div>
                    <button class="play"><i class="fas fa-play"></i> Play</button>
                    <button class="info"><span class="circle">i</span> <span>More Info</span></button>
                </div>
            </section>
        </div>

       
        <ul>
            <li v-for="(home, index) in home" :key="index">
                <!-- A card gli passo tutto l'oggettone che rappresenta il film  nella home-->
                <Card :details="home"/>
            </li>
        </ul>
        

        <h2>Film:</h2>
        <ul>
            <li v-for="(film, index) in films" :key="index">
                <!-- A card gli passo tutto l'oggettone che rappresenta il film -->
                <Card :details="film"/>
            </li>
        </ul>

        <h2>Serie tv:</h2>
        <ul>
            <li v-for="(serie, index) in series" :key="index">
                <!-- A card gli passo tutto l'oggettone che rappresenta la serie -->
                <Card :details="serie"/>
            </li>
        </ul>
    </div>
</template>

<script>
import Card from './Card.vue';
import axios from 'axios';

export default {
    name: 'Films',
    props: ['films', 'series', 'home'],
    components: {
        Card
    },
    created() {
          // Effettuo una nuova chiamata per la home
        axios.get('https://api.themoviedb.org/3/search/movie?api_key=dfb070b958255d617f646fa427b32530&language=it_IT&query=code', {
        params: {
          api_key: 'aad62cbe2fe92d75516ca3bc33211c38',
          language: 'it-IT'
        }
      })
      .then((response) => {
        // 6) Salvo i dati results in home
        this.home = response.data.results;
      });
    }
}
</script>

<style lang="scss" scoped>
    .movies-container{
        background-color: rgb(20, 20, 20);
        .trailer{
            section{
                position: relative;
                iframe{
                    width: 100%;
                    height: 700px;
                }
                .dettagli-video{
                    position: absolute;
                    left: 50px;
                    bottom: 150px;
                    width: 600px;
                    .trama{
                        color: white;
                        font-size: 20px;
                        font-family: 'Poppins', sans-serif;
                        padding-top: 10px;
                    }
                    .play{
                        background-color: white;
                        border-radius: 5px;
                        padding: 12px 27px;
                        border: none;
                        color: black;
                        font-size: 18px;
                        font-weight: bold;
                        margin: 20px 10px 0 0;
                        cursor: pointer;
                        i{
                            padding-right: 5px;
                        }
                    }
                    .info{
                        background-color: #7c7b7b;
                        opacity: 0.8;
                        border-radius: 5px;
                        padding: 12px 27px;
                        border: none;
                        color: white;
                        font-size: 18px;
                        font-weight: bold;
                        cursor: pointer;
                        .circle{
                            padding: 0 7px;
                            border: 3px solid white;
                            border-radius: 50%;
                            margin-right: 8px;
                        }
                    }
                }
                .dettagli-video .play:hover{
                    opacity: 0.7;
                }
                .dettagli-video .info:hover{
                    opacity: 0.6;
                }
            }
        }
        h2{
            padding: 30px 0 0 30px;
            color: rgb(233, 233, 233);
            font-family: 'Poppins', sans-serif;
        }
        ul{
            display: flex;
            flex-wrap: wrap;
            li{
                margin: 50px 30px 0 0;
                list-style: none;
            }
        }
        .lista-home{
            h3{
                color: rgb(233, 233, 233);
                font-family: 'Poppins', sans-serif;
            }
        }
    }
</style>
<template>
    <!-- Stampiamo i dati interessati utilizzando la props, tramite la condizione stampo i dati relativi al film o alla serie tv -->
    <div class="card">

        <img v-if="details.poster_path" :src= "`https://image.tmdb.org/t/p/w342/${details.poster_path}`">
        <img v-else :src= "`https://d1csarkz8obe9u.cloudfront.net/posterpreviews/netflix-movie-series-template-design-e71bfb50a083bc6cb974024bb0bca100_screen.jpg?ts=1605596553`">

        <div class="testo-img">
            <!-- Se è presente details.title allora stampo details.title altrimenti stampo details.name-->
            <h3 v-if="details.title">Titolo: {{details.title}}</h3>
            <h3 v-else> Titolo: {{details.name}}</h3>
            <!-- Oppure <h3>{{details.title || details.name}}</h3> -->
            
            <!-- Se è presente dtails.original_title allora stampo details.original_title altrimenti stampo details.original_name-->
            <h3>Titolo originale: {{details.original_title ? details.original_title : details.original_name}}</h3>
            <!-- Oppure: <h3> Titolo originale: {{details.original_title ||  details.original_name}} </h3> -->

            <div>Lingua: <lang-flag :iso='details.original_language'/></div>
            <!-- Utilizzo math.round per arrottondare il numero ad una cifra e divido per due così da avere un numero da 1 a 5 (essendo da 1 a 10 di partenza) -->
            <div>Voto: {{Math.round(details.vote_average/2)}}
                <i v-for="(star, index) in Math.round(details.vote_average / 2)" in :key="index" class="fas fa-star"></i>
                <i v-for="(star, index) in Math.round(5 - details.vote_average / 2)" in :key="index" class="far fa-star"></i>
            </div>

            <div class="overview">
               <span v-if="details.overview"><strong>Overview:</strong> {{details.overview}}</span>
            </div>
        </div>
    </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';

export default {
    name: "Card",
    props: ['details'],
    components: {
        LangFlag
    }
}
</script>

<style lang="scss" scoped>
.card:hover img{
    opacity: 0.2;
}
.card{
    width: 300px;
    position: relative;
    img{
        width: 300px;
        height: 450px;
        object-fit: cover;
        object-position: center;
        cursor: pointer;
    }
    .testo-img{
        display: none;
        position: absolute;
        top: 0;
        left: 10px;
        height: 100%;
        overflow: scroll;
    }
    .overview{
        span{
            font-size: 13px;
        }
    }
}
.card:hover .testo-img{
        display: block;
        i{
        color: rgb(255, 238, 0);
        }
        h3{
            color: rgb(233, 233, 233);
            font-family: 'Poppins', sans-serif;
        }
        div{
            color: rgb(233, 233, 233);
            font-family: 'Poppins', sans-serif;
        }
    }



</style>
<template>
    <!-- Stampiamo i dati interessati utilizzando la props, tramite la condizione stampo i dati relativi al film o alla serie tv -->
    <div class="card">
        <img :src= "`https://image.tmdb.org/t/p/w500/${details.poster_path}`">
        <h3 v-if="details.title">Titolo: {{details.title}}</h3>
        <h3 v-else> Titolo: {{details.name}}</h3>
        <h3>Titolo originale: {{details.original_title ? details.original_title : details.original_name}}</h3>
        <div>Lingua: <lang-flag :iso='details.original_language'/></div>
        <div>Voto: {{details.vote_average.toFixed(0)/2}}</div>
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
.card{
    width: 300px;
    img{
        width: 300px;
    }
}

</style>
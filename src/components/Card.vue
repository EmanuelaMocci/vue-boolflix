<template>
    <!-- Stampiamo i dati interessati utilizzando la props, tramite la condizione stampo i dati relativi al film o alla serie tv -->
    <div class="card">
        <h3 v-if="details.title">{{details.title}}</h3>
        <h3 v-else>{{details.name}}</h3>
<hr>
        <h4>{{details.original_title ? details.original_title : details.original_name}}</h4>
        <div><lang-flag :iso='details.original_language'/></div>
        <div>{{details.vote_avarage}}</div>
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
<template>
    <!-- Stampiamo i dati interessati utilizzando la props -->
    <div class="card">
        <h3>{{details.title}}</h3>
        <h4>{{details.original_title}}</h4>
        <div>{{details.original_language}}</div>
        <div>{{details.vote_avarage}}</div>
    </div>
</template>

<script>
export default {
    name: "Card",
    props: ['details']
}
</script>
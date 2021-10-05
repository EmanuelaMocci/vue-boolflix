<template>
    <div class="header">
        <input type="text" placeholder="Inserisci il titolo di un film">
        <button>Cerca</button>
    </div>
</template>

<script>

export default {
        name: 'Header',
    }

</script>

<style lang="scss" scoped>

.header{
    height: 80px;
    background-color: black;
    display: flex;
    align-items: center;
    justify-content: flex-end;
    padding-right: 50px;
    
    input{
        padding: 10px;
        width: 200px;
        height: 20px;
    }
    button{
        padding: 10px;
        height: 44px;
    }
}

</style>

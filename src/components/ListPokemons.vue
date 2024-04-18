<script setup>
    const pokemon = defineProps(["name", "url"])
    const idPokemon = pokemon.url.split('/')[6]
    const imageUrl = "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/"+idPokemon+".png"
    
</script>

<template>
    <div class="col-md-4">
        <div class="card mb-3">
        <img :src="imageUrl" alt="..." class="card-img-top">
        <div class="card-body">
            <p class="card-title">{{ pokemon.name }}</p>
            <p class="card-text">{{ pokemon.url }}</p>
        </div>
    </div>
    </div>
</template>

<style>

</style>
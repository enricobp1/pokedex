<script setup>
// props - onMounted, reactive, ref
import { onMounted, reactive, ref } from 'vue';
import ListPokemons from '../components/ListPokemons.vue';

let pokemons = reactive(ref())

// fetch - axios
onMounted(() => {
  fetch("https://pokeapi.co/api/v2/pokemon?limit=1000$offset=0")
  .then(response => response.json())
  .then(response => {
    pokemons.value = response.results
    console.log(pokemons)
  });
})

</script>

<template>
  <main>
    <div class="containter">
      <div class="row mt-4">
        <div class="col-sm12 col-md-6">
          <div class="card" style="width: 24em;">
            <img src="https://assets.pokemon.com/assets/cms2/img/pokedex/full/475.png" alt="..." class="card-img-top">
            <div class="card-body">
              <h5 class="card-title">Card title</h5>
              <p class="card-text">Um texto resumido e pequeno aqui!</p>
            </div>
          </div>
        </div>
        <div class="col-sm12 col-md-6">
          <div class="card">
            <div class="card-body row">
              <ListPokemons
            v-for="pokemon in pokemons"            
            :key="pokemon.name"
            :name="pokemon.name"
            :url="pokemon.url"
            >
          </ListPokemons>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

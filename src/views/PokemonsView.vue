<script setup>
    import { useGetData } from '@/composables/getData'
    import NamedPokemonsView from './NamedPokemonsView.vue'

    const { data, getData, loading } =  useGetData()

    getData('https://pokeapi.co/api/v2/pokemon')
    
</script>

<template>
    <h1>Pokemons</h1>
    <p v-if="loading">Cargando información...</p>
    <div v-if="data">
        <NamedPokemonsView
        v-for="(item, index) in data.results"
        :key="index"
        :NombrePokemon = "item"
    >
    </NamedPokemonsView>
    <div class="mt-2">
        <button 
            :disabled = "!data.previous"
            class="btn btn-success me-2" 
            @click="getData(data.previous)">Previous
        </button>
        <button 
            :disabled = "!data.next"
            class="btn btn-primary" 
            @click="getData(data.next)">Next
        </button>
    </div>
    
    </div>
    
</template>
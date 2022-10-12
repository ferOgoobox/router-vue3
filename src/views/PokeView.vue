<script setup>
import { useGetData } from '@/composables/getData'
import { useRoute, useRouter } from 'vue-router'
import { useFavoritoStore } from '@/store/favoritos.js'

const route = useRoute()
const router = useRouter()

const useFavoritos = useFavoritoStore()
const { add, findPoke } = useFavoritos

const back = () =>{
    router.push('/pokemons')
}
const { data, getData, loading } = useGetData()

getData(`https://pokeapi.co/api/v2/pokemon/${route.params.name}`)

</script>

<template>
    <p v-if="loading">Cargando información...</p>
    <div v-if="data">
        <img :src="data.sprites?.front_default" alt="">
        <h1>Poke name: {{ $route.params.name }}</h1>
        <button :disabled="findPoke(data.name)" @click="add(data)" class="btn btn-primary mb-2">Agregar Favorito</button>
    </div>
    <h1 v-else>No existe el pokemon</h1>
    <button @click="back" class="btn btn-outline-primary">Volver</button>
</template>
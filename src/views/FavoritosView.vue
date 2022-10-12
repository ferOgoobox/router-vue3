<script setup>
import { useFavoritoStore } from '@/store/favoritos.js'
import { storeToRefs } from 'pinia';

const useFavoritos = useFavoritoStore()
const { remove } = useFavoritos 
const { favoritos } = storeToRefs(useFavoritos)


</script>

<template>
    <h1>Favoritos</h1>
    <p v-if="favoritos.length == 0">Sin favoritos</p>
    <ul class="list-group" v-else>
        <li
            class="list-group-item"
            v-for="(item,index) in favoritos"
            :key="item.id"        
        >
        <div>
            {{ item.name }}
        </div>
        <router-link
            class = "btn btn-primary mb-2"
            :to="`/pokemons/${item.name}`"
        >
            Mayor Información
        </router-link>
        
        <div>
            <button @click="remove(item.id)" class="btn btn-danger"> Eliminar</button>
        </div>
        </li>
    </ul>
</template>
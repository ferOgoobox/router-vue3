<script setup>
    import { RouterLink } from 'vue-router'

    defineProps(['NombrePokemon'])
</script>

<template>
    <ul class="list-group">
        <li class="list-group-item">
        <RouterLink :to="`/pokemons/${NombrePokemon.name}`">
            {{ NombrePokemon.name }}</RouterLink>
        </li>
    </ul>
</template>
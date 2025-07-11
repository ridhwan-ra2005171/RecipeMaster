<script setup lang="ts">
import type { RecipeResponse } from '~~/types/types';


const {recipeId} = useRoute().params;

const {data, error} = await useFetch<RecipeResponse>(`https://dummyjson.com/recipes/${recipeId}`);

</script>

<template>
  <div>
    <h1 class="text-4xl">{{ recipeId }}</h1>
  </div>
</template>

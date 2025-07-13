<script setup lang="ts">
import { type Recipe } from "../../types/types";

defineProps<{
  recipe: Recipe;
}>();
</script>

<template>
  <div class="shadow rounded-md dark:bg-gray-700">
    <NuxtImg
      sizes="xs:100vw sm:50vw lg:400px"
      format="webp"
      densities="x1"
      :src="recipe.image"
      alt=""
      class="rounded-t-md"
    />
    <div class="flex flex-col py-6 px-4">
      <p class="text-2xl font-semibold mb-2">{{ recipe.name }}</p>
      <div class="font-normal w-full  flex gap-8 text-xl mb-4">
        <div class="flex items-center gap-1">
          <Icon name="mdi:clock-time-eight-outline" style="color: #f79f1a" />
          <span>{{ recipe.cookTimeMinutes }}</span>
        </div>
        <div class="flex items-center gap-1">
          <Icon name="mdi:fire" style="color: #f79f1a" />
          <span>{{ recipe.caloriesPerServing }}</span>
        </div>
        <div class="flex items-center gap-1">
          <Icon name="mdi:star" style="color: #f79f1a" />
          <span>{{ recipe.rating }} ({{ recipe.reviewCount }})</span>
        </div>
      </div>
      <!-- <button
        class="px-4 py-2 text-white self-start bg-dodgeroll-gold rounded-md text-base lg:text-lg cursor-pointer"
      >
        View
      </button> -->
      <BaseBtn :to="`/recipes/${recipe.id}`" label="View Recipe"  />
    </div>
  </div>
</template>
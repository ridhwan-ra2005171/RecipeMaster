<script setup lang="ts">
import { NuxtImg } from "#components";
import { type RecipeResponse } from "~~/types/types";

// const {data, error} = useAsyncData('recipes', () => $fetch('https://dummyjson.com/recipes?limit=20'));
//for basic usages, just use useFetch

const { data, error } = await useFetch<RecipeResponse>(
  "https://dummyjson.com/recipes?limit=66"
);

// Sorting state
const sortBy = ref('name'); // 'name' or 'prepTime'
const sortOrder = ref('asc'); // 'asc' or 'desc'

// Search state
const searchQuery = ref('');

// Computed property for filtered and sorted recipes
const filteredAndSortedRecipes = computed(() => { 
  if (!data.value?.recipes) return [];
  
  let recipes = [...data.value.recipes];
  
  // Filter by search query
  if (searchQuery.value.trim()) {
    const query = searchQuery.value.toLowerCase().trim();
    recipes = recipes.filter(recipe => 
      recipe.name.toLowerCase().includes(query) ||
      recipe.cuisine.toLowerCase().includes(query) ||
      recipe.tags.some(tag => tag.toLowerCase().includes(query)) ||
      recipe.ingredients.some(ingredient => ingredient.toLowerCase().includes(query))
    );
  }
  
  // Sort recipes
  return recipes.sort((a, b) => {
    let comparison = 0;
    
    if (sortBy.value === 'name') {
      comparison = a.name.localeCompare(b.name);
    } else if (sortBy.value === 'prepTime') {
      comparison = a.cookTimeMinutes - b.cookTimeMinutes;
    }
    
    return sortOrder.value === 'asc' ? comparison : -comparison;
  });
});

// Function to handle sort change
const handleSortChange = (newSortBy: string) => {
  if (sortBy.value === newSortBy) {
    // Toggle order if same sort field
    sortOrder.value = sortOrder.value === 'asc' ? 'desc' : 'asc';
  } else {
    // Reset to ascending for new sort field
    sortBy.value = newSortBy;
    sortOrder.value = 'asc';
  }
};

// Function to scroll to recipes section
const scrollToRecipes = () => {
  const recipesSection = document.getElementById('recipes-section');
  if (recipesSection) {
    recipesSection.scrollIntoView({ 
      behavior: 'smooth',
      block: 'start'
    });
  }
};

useSeoMeta({
  title: "Nuxtcipes",
  description: "Recipes for you to cook!",
  ogTitle: "Nuxtcipes",
  ogDescription: "Recipes for you to cook!",
  ogImage: "/nuxt-course-hero.png",
  ogUrl: `http:localhost:3000`,
  twitterTitle: "Nuxtcipes",
  twitterDescription: "Recipes for you to cook!",
  twitterImage: "nuxt-course-hero.png",
  twitterCard: "summary",
});
</script>

<template>
  <main>
    <section class="bg-[#f1f1f1]">
      <div
        class="container flex flex-col lg:flex-row items-center py-20 gap-10"
      >
        <div class="flex-1 order-2 lg:order-1 text-center lg:text-left">
          <h1 class="text-4xl lg:text-6xl font-extrabold mb-6 text-balance">
            Master the Kitchen with Ease: Unleash Your Inner Chef Today!
          </h1>
          <p class="text-xl lg:text-2xl mb-8 text-balance">
            Discover recipes helping you to find the easiest way to cook.
          </p>
          <button
            @click="scrollToRecipes"
            class="px-4 py-2 text-white self-start bg-dodgeroll-gold rounded-md text-lg cursor-pointer hover:bg-opacity-90 transition-colors"
          >
            Browse Recipes
          </button>
        </div>
        <div class="flex-1 order-1 lg:order-2">
          <NuxtImg
            src="/nuxt-course-hero.png"
            alt=""
            densities=""
            sizes="xs:100vw sm:667px"
            format="webp"
          />
        </div>
      </div>
    </section>
    <section id="recipes-section" class="py-20 container">
            <div class="flex flex-col lg:flex-row lg:items-center lg:justify-between mb-8">
        <div>
          <h2 class="text-3xl lg:text-5xl mb-2">Discover, Create, Share</h2>
          <p class="text-lg lg:text-xl">Check out our most popular recipes!</p>
        </div>
      </div>
      
      <!-- Search and Sort Controls -->
      <div class="mb-8 flex flex-col lg:flex-row lg:items-center lg:justify-between gap-4">
        <!-- Search Bar -->
        <div class="flex-1 max-w-lg">
          <div class="relative">
            <input
              v-model="searchQuery"
              type="text"
              placeholder="Search recipes by name, cuisine, tags, or ingredients..."
              class="w-full px-4 py-3 pl-10 pr-4 text-gray-900 bg-white border border-gray-300 rounded-lg focus:ring-2 focus:ring-dodgeroll-gold focus:border-transparent outline-none transition-all"
            />
            <div class="absolute inset-y-0 left-0 flex items-center pl-3 pointer-events-none">
              <svg class="w-5 h-5 text-gray-400" fill="none" stroke="currentColor" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"></path>
              </svg>
            </div>
          </div>
          <p v-if="searchQuery" class="mt-2 text-sm text-gray-600">
            Found {{ filteredAndSortedRecipes.length }} recipe{{ filteredAndSortedRecipes.length !== 1 ? 's' : '' }}
          </p>
        </div>
        
        <!-- Sort Controls -->
        <div class="flex items-center gap-4">
          <label for="sort-select" class="text-sm font-semibold text-gray-700">Sort by:</label>
          <div class="flex items-center gap-2">
            <button
              @click="handleSortChange('name')"
              :class="[
                'px-3 py-1 rounded-md text-sm font-medium transition-colors',
                sortBy === 'name' 
                  ? 'bg-dodgeroll-gold text-white' 
                  : 'bg-gray-200 text-gray-700 hover:bg-gray-300'
              ]"
            >
              Name
              <span v-if="sortBy === 'name'" class="ml-1">
                {{ sortOrder === 'asc' ? '↑' : '↓' }}
              </span>
            </button>
            <button
              @click="handleSortChange('prepTime')"
              :class="[
                'px-3 py-1 rounded-md text-sm font-medium transition-colors',
                sortBy === 'prepTime' 
                  ? 'bg-dodgeroll-gold text-white' 
                  : 'bg-gray-200 text-gray-700 hover:bg-gray-300'
              ]"
            >
              Prep Time
              <span v-if="sortBy === 'prepTime'" class="ml-1">
                {{ sortOrder === 'asc' ? '↑' : '↓' }}
              </span>
            </button>
          </div>
        </div>
      </div>
      
      <div
        v-if="!error"
        class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-x-4 gap-y-8"
      >
        <RecipeCard v-for="recipe in filteredAndSortedRecipes" :recipe="recipe" />
      </div>
      <p v-else class="text-xl">
        Oops, something went wrong. Please try again.
      </p>
    </section>
  </main>
</template>

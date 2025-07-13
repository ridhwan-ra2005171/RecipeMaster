<script setup lang="ts">
import { NuxtLink } from '#components';

const colorMode = useColorMode();

const toggleColorMode = () => {
  colorMode.preference = colorMode.value === 'dark' ? 'light' : 'dark';
};
</script>

<template>
  <header class="py-2 border-b">
    <nav class="flex container items-center">
      <NuxtLink to="/" class="flex gap-1 items-center">
        <NuxtImg width="56px" densities="2x" src="/icon-green.png" alt="" format="webp"/>
        <span class="text-3xl font-bold">Nuxtcipes</span>
      </NuxtLink>
      <ul class="flex gap-6 ml-auto text-xl font-bold capitalize items-center">
        <li>
          <NuxtLink to="/">Home</NuxtLink>
        </li>
        <li>
          <NuxtLink to="/about">About</NuxtLink>
        </li>
        <li>
          <button 
            @click="toggleColorMode" 
            class="p-2 rounded-full hover:bg-gray-100 dark:hover:bg-gray-800 transition-all duration-200 hover:scale-110 flex items-center justify-center"
            :aria-label="colorMode.value === 'dark' ? 'Switch to light mode' : 'Switch to dark mode'"
          >
            <Icon 
              :name="colorMode.value === 'dark' ? 'heroicons:sun' : 'heroicons:moon'" 
              class="w-6 h-6"
            />
          </button>
        </li>
      </ul>
    </nav>
  </header>
</template>

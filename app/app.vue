<template>
  <div class="font-Montserrat">
    <NuxtLayout>
      <NuxtPage />
    </NuxtLayout>
  </div>
</template>
<!-- tailwindCSS.experimental.configFile remove this -->

<style>
html.dark{
  color-scheme: dark;
}

body{
  @apply bg-slate-50 text-slate-800 dark:bg-slate-800 dark:text-slate-100
}
</style>

<script setup lang="ts"></script>

<template>
  <main>
    <section class="container mx-auto max-w-4xl px-4 py-20">
      <!-- Title -->
      <h1
        class="text-4xl md:text-6xl font-extrabold bg-gradient-to-r from-orange-500 via-orange-400 to-yellow-300 text-transparent bg-clip-text mb-4"
      >
        RecipeMaster
      </h1>

      <!-- Author Link -->
      <p class="text-lg text-muted mb-6">
        Made by:
        <a
          href=""
          target="_blank"
          class="text-accent underline hover:text-primary transition-colors duration-200"
        >
          Ridhwan Athaullah
        </a>
      </p>

      <!-- Description -->
      <p
        class="text-base text-slate-700 dark:text-slate-300 mb-10 leading-relaxed"
      >
        RecipeMaster is a modern web application for discovering and exploring a
        wide variety of recipes. Built with Nuxt 3 and styled with Tailwind CSS,
        this project showcases an interactive, data-driven user interface. It
        fetches recipe data from the DummyJSON API and presents it in a clean,
        responsive layout.
      </p>

      <!-- Features -->
      <h2 class="text-2xl font-bold text-content mb-3">Features</h2>
      <ul class="list-disc list-inside space-y-2 text-muted mb-10">
        <li>
          <strong>Recipe Discovery:</strong> Grid of recipes fetched from the
          DummyJSON API.
        </li>
        <li>
          <strong>Detailed View:</strong> View full recipe details including
          ingredients and instructions.
        </li>
        <li>
          <strong>Advanced Search:</strong> Filter by name, cuisine, tags, or
          ingredients.
        </li>
        <li>
          <strong>Sorting:</strong> Sort recipes by name or prep time
          (ascending/descending).
        </li>
        <li>
          <strong>Dark Mode:</strong> Toggleable theme using
          <code>@nuxtjs/color-mode</code>.
        </li>
        <li>
          <strong>Responsive Design:</strong> Works beautifully across all
          screen sizes.
        </li>
        <li>
          <strong>SEO:</strong> Meta tag generation via Nuxt's
          <code>useSeoMeta</code>.
        </li>
      </ul>

      <!-- Tech Stack -->
      <h2 class="text-2xl font-bold text-content mb-3">Tech Stack</h2>
      <ul class="list-disc list-inside space-y-2 text-muted">
        <li><strong>Framework:</strong> Nuxt 3</li>
        <li><strong>UI Library:</strong> Vue 3</li>
        <li><strong>Styling:</strong> Tailwind CSS</li>
        <li><strong>Language:</strong> TypeScript</li>
        <li><strong>Data Source:</strong> DummyJSON API</li>
        <li>
          <strong>Modules:</strong>
          <ul class="list-disc list-inside ml-5 mt-1 space-y-1">
            <li><code>@nuxt/image</code> – Optimized image handling</li>
            <li><code>@nuxt/icon</code> – Icon integration</li>
            <li><code>@nuxtjs/google-fonts</code> – Montserrat font support</li>
            <li><code>@nuxtjs/color-mode</code> – Theme switching</li>
          </ul>
        </li>
      </ul>
    </section>
  </main>
</template>

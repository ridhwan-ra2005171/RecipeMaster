<template>
  <div class="font-Montserrat">
    <NuxtLayout>
      <NuxtPage />
    </NuxtLayout>
  </div>
</template>

<style>
/* Set custom theme variables for light mode */
:root {
  --color-primary: #166534;
  --color-muted: #e5e5e5;
  --color-tertiary: #94a3b8;
  --color-surface: #ffffff;
  --color-accent: #64748b;
  --color-secondary: #dcfce7;
  --color-content: #0f172a;
  --color-background: #f8fafc;
}

/* Override theme variables for dark mode */
html.dark {
  color-scheme: dark;

  --color-primary: #4ade80;
  --color-muted: #334155;
  --color-tertiary: #64748b;
  --color-surface: #1e293b;
  --color-accent: #94a3b8;
  --color-secondary: #064e3b;
  --color-content: #f1f5f9;
  --color-background: #0f172a;
}

body {
  @apply bg-[var(--color-background)] text-[var(--color-content)];
}
</style>

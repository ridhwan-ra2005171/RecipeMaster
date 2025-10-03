# RecipeMaster
RecipeMaster is a modern web application for discovering and exploring a wide variety of recipes. Built with Nuxt 3 and styled with Tailwind CSS, this project serves as a showcase for building interactive, data-driven web applications. It fetches recipe data from the DummyJSON API and presents it in a clean, user-friendly interface.

## Features

-   **Recipe Discovery:** Fetches and displays a grid of recipes from the DummyJSON API.
-   **Detailed View:** Click on any recipe to see its full details, including ingredients and step-by-step instructions.
-   **Advanced Search:** Dynamically filter recipes by name, cuisine, tags, or ingredients.
-   **Sorting Functionality:** Sort the recipe list by name or preparation time in both ascending and descending order.
-   **Dark Mode:** A sleek dark mode toggle for comfortable nighttime browsing, powered by `@nuxtjs/color-mode`.
-   **Responsive Design:** A fully responsive interface that works seamlessly on desktop, tablet, and mobile devices.
-   **SEO Optimized:** Utilizes Nuxt's `useSeoMeta` for dynamic meta tags on recipe detail pages.

## Tech Stack

-   **Framework:** [Nuxt 3](https://nuxt.com/)
-   **UI Library:** [Vue 3](https://vuejs.org/)
-   **Styling:** [Tailwind CSS](https://tailwindcss.com/)
-   **Language:** [TypeScript](https://www.typescriptlang.org/)
-   **Data Source:** [DummyJSON API](https://dummyjson.com/docs/recipes)
-   **Modules:**
    -   `@nuxt/image` for optimized image handling.
    -   `@nuxt/icon` for easy access to a wide range of icons.
    -   `@nuxtjs/google-fonts` for integrating the Montserrat font family.
    -   `@nuxtjs/color-mode` for theme switching.

## Getting Started

Follow these instructions to get a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

You need to have [Node.js](https://nodejs.org/en) (v18.0.0 or newer) installed on your system.

### Installation

1.  Clone the repository:
    ```bash
    git clone https://github.com/ridhwan-ra2005171/RecipeMaster.git
    ```
2.  Navigate to the project directory:
    ```bash
    cd RecipeMaster
    ```
3.  Install dependencies using your preferred package manager:

    ```bash
    # npm
    npm install

    # pnpm
    pnpm install

    # yarn
    yarn install
    ```

### Running the Application

**Development Server**

Start the development server on `http://localhost:3000`:

```bash
# npm
npm run dev

# pnpm
pnpm dev

# yarn
yarn dev
```

**Production**

Build the application for production:

```bash
# npm
npm run build

# pnpm
pnpm build

# yarn
yarn build
```

Locally preview the production build:

```bash
# npm
npm run preview

# pnpm
pnpm preview

# yarn
yarn preview
```

## Project Structure

-   `app/`: Contains the core application logic.
    -   `components/`: Reusable Vue components like `RecipeCard.vue` and `BaseNavigation.vue`.
    -   `layouts/`: Defines the main application layouts, such as `default.vue`.
    -   `pages/`: Manages the application's routing.
        -   `index.vue`: The homepage.
        -   `recipes/[id].vue`: A dynamic route for individual recipe detail pages.
-   `public/`: Stores static assets that are publicly accessible.
-   `types/`: Contains TypeScript type definitions, like the `Recipe` interface.
-   `nuxt.config.ts`: The main configuration file for Nuxt, where modules and project settings are defined.

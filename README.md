
# Nuxt 3 Project Setup with Quasar, Pinia, and Routing

This guide walks through setting up a Nuxt 3 project with Quasar, Pinia, and routing. This is for creating a frontend dashboard with simple login, forgot password logic, and basic caching capabilities. The routing mechanism will cover three pages: `login`, `dashboard`, and a dynamic user page `/:userId`.

Login, forgot password like endpoint will be provided later. Assume they exist.

App Name: AI - HR
Instagram Login Page is a good implementation for login page.

## Setup Quasar in Nuxt Project

1. In your `nuxt.config.ts`, add Quasar to the `build` section:
   ```typescript
   export default defineNuxtConfig({
     build: {
       transpile: ['quasar'],
     },
     css: ['quasar/dist/quasar.css'],
   })
   ```

2. Import Quasar components where needed in your project (e.g., `quasar` for UI components).

## Set Up Pinia for State Management

1. Create a Pinia store for managing states (e.g., authentication state).

   In `store/index.ts`:
   ```typescript
   import { defineStore } from 'pinia';

   export const useAuthStore = defineStore('auth', {
     state: () => ({
       user: null as any,
     }),
     actions: {
       setUser(user: any) {
         this.user = user;
       },
       clearUser() {
         this.user = null;
       },
     },
   });
   ```

## Implement Routing

1. In `pages/`, create the following files:
   - `login.vue` (for login page)
   - `dashboard.vue` (for dashboard page)
   - `[userId].vue` (dynamic user page)

2. Routing will be automatically handled by Nuxt. It supports file-based routing, and it will look for pages in the `pages/` folder. Here's how the routing works:
   - `/login` → `pages/login.vue`
   - `/dashboard` → `pages/dashboard.vue`
   - `/:userId` → `pages/[userId].vue`

## Use TypeScript with Script Setup

Make sure each page has the `script setup` syntax using TypeScript. Here's an example for `login.vue`:

```vue
<script setup lang="ts">
import { ref } from 'vue';

const email = ref('');
const password = ref('');

const login = () => {
  // Perform login logic
}
</script>
```

Repeat this setup for other pages as necessary.

## Implement Login and Forgot Password Logic

You can implement the login and forgot password logic in the `login.vue` component. Here is a simple structure:

1. `login.vue`: Collect username and password, use the Pinia store to manage state.
2. `forgot-password.vue`: Create a form for the user to reset their password.

## Caching with Pinia

Pinia can handle caching by storing the authentication state across different pages. Use actions like `setUser` and `clearUser` to cache data during login and logout.

## Conclusion

This is a basic setup for building a Nuxt 3 app using Quasar, Pinia, and routing. You can now build out the UI components using Quasar, implement login and authentication logic, and handle user-specific data on the dashboard.

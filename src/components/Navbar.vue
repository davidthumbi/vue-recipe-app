<template>
  <header class="bg-white shadow h-24 flex justify-between items-center px-5 md:px-10">
    <!-- Logo -->
    <router-link :to="{ name: 'home' }" class="inline-flex items-center h-full text-orange-500 font-bold">
      <img src="../assets/logo.png" alt="alt" class="h-20" />
    </router-link>

    <!-- Desktop Navigation Links (Visible on Larger Screens) -->
    <nav class="hidden md:flex gap-4 text-orange-500">
      <router-link :to="{ name: 'byName' }" class="px-4 py-2 transition-colors hover:bg-orange-500 hover:text-white">
        Search Meals
      </router-link>
      <router-link :to="{ name: 'byLetter' }" class="px-4 py-2 transition-colors hover:bg-orange-500 hover:text-white">
        Meals By Letter
      </router-link>
      <router-link :to="{ name: 'ingredients' }" class="px-4 py-2 transition-colors hover:bg-orange-500 hover:text-white">
        Meals By Ingredients
      </router-link>
    </nav>

    <!-- Mobile Menu Button (Visible on Smaller Screens) -->
    <button 
      @click="isOpen = !isOpen" 
      class="md:hidden text-orange-500 p-2 focus:outline-none focus:ring-2 focus:ring-orange-500">
      <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
      </svg>
    </button>

    <!-- Mobile Dropdown Menu -->
    <div v-if="isOpen" class="absolute top-24 left-0 w-full bg-white shadow-lg md:hidden">
      <nav class="flex flex-col items-start p-4 text-orange-500">
        <router-link 
          @click="closeMenu" 
          :to="{ name: 'byName' }" 
          class="w-full px-4 py-3 transition-colors hover:bg-orange-500 hover:text-white rounded-md">
          Search Meals
        </router-link>
        <router-link 
          @click="closeMenu" 
          :to="{ name: 'byLetter' }" 
          class="w-full px-4 py-3 transition-colors hover:bg-orange-500 hover:text-white rounded-md">
          Meals By Letter
        </router-link>
        <router-link 
          @click="closeMenu" 
          :to="{ name: 'ingredients' }" 
          class="w-full px-4 py-3 transition-colors hover:bg-orange-500 hover:text-white rounded-md">
          Meals By Ingredients
        </router-link>
      </nav>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      isOpen: false, // Controls the visibility of the mobile dropdown menu
    };
  },
  methods: {
    closeMenu() {
      this.isOpen = false; // Closes the menu when a link is clicked
    },
  },
  watch: {
    // Closes the menu when navigating to a different route
    $route() {
      this.isOpen = false;
    },
  },
};
</script>

<style scoped>
/* Basic styling for responsiveness */
@media (min-width: 768px) {
  .absolute {
    display: none; /* Hide the mobile dropdown on larger screens */
  }
}
</style>

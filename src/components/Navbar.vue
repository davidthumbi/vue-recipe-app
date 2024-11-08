<template>
  <header class="bg-white shadow h-24 flex justify-between items-center px-5 md:px-10">
    <!-- Logo -->
    <router-link :to="{ name: 'home' }" class="inline-flex items-center h-full text-orange-500 font-bold">
      <img src="../assets/logo.png" alt="alt" class="h-20" />
    </router-link>

    <!-- Hamburger Button (Visible on Mobile) -->
    <button 
      @click="isOpen = !isOpen" 
      class="md:hidden text-orange-500 p-2 focus:outline-none focus:ring-2 focus:ring-orange-500">
      <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
      </svg>
    </button>

    <!-- Navigation Links (Responsive) -->
    <nav :class="['flex-col', 'md:flex-row', 'items-center', 'gap-1', 'text-orange-500', 'md:flex', isOpen ? 'flex' : 'hidden']" class="flex md:flex items-center">
      <router-link :to="{ name: 'byName' }" class="px-2 py-2 md:py-0 transition-colors hover:bg-orange-500 hover:text-white">
        Search Meals
      </router-link>
      <router-link :to="{ name: 'byLetter' }" class="px-2 py-2 md:py-0 transition-colors hover:bg-orange-500 hover:text-white">
        Meals By Letter
      </router-link>
      <router-link :to="{ name: 'ingredients' }" class="px-2 py-2 md:py-0 transition-colors hover:bg-orange-500 hover:text-white">
        Meals By Ingredients
      </router-link>
    </nav>
  </header>
</template>

<script>
export default {
  data() {
    return {
      isOpen: false, // controls the visibility of the mobile menu
    };
  },
  watch: {
    // Close the menu when resizing to desktop
    $route() {
      this.isOpen = false;
    },
  },
};
</script>

<style scoped>
/* Add responsive styling to control the display of the nav links */
@media (min-width: 768px) {
  nav {
    display: flex !important; /* Ensures the nav menu is displayed on larger screens */
  }
}
</style>

<template>
  <a
    :href="href"
    target="_blank"
    class="flex items-center px-4 py-2 rounded-full bg-red-600 text-white font-semibold hover:bg-red-700 transition-colors"
  >
    <!-- YouTube Icon -->
    <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5 mr-2" viewBox="0 0 24 24" fill="currentColor">
      <path d="M19.635 6.438a2.815 2.815 0 00-1.98-1.99C15.646 4 12 4 12 4s-3.646 0-5.655.448a2.815 2.815 0 00-1.98 1.99A29.877 29.877 0 004 12c0 1.983.219 3.953.365 5.563a2.815 2.815 0 001.98 1.99C8.354 20 12 20 12 20s3.646 0 5.655-.448a2.815 2.815 0 001.98-1.99C19.781 15.953 20 13.983 20 12c0-1.983-.219-3.953-.365-5.563zM10 15V9l5 3-5 3z"/>
    </svg>
    
    <!-- Button Text -->
    <span><slot>YouTube</slot></span>
  </a>
</template>

<script setup>
const props = defineProps({
  href: String
})
</script>

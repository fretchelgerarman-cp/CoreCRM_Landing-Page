<script>
import { Menu } from '@lucide/vue'

export default {
    components: {
        Menu
    },

    data() {
        return {
            isOpen: false
        }
    },

    methods: {
        toggleMenu() {
            this.isOpen = !this.isOpen
        }
    }
}
</script>

<template>
  <nav class="bg-white shadow-sm sticky top-0 z-50">
    <div class="max-w-7xl mx-auto px-4">
      <div class="flex justify-between h-16 items-center">
        
     
        <div class="text-xl font-bold text-(--emerald-dark)">
            <span class="bg-(--emerald) text-white px-2  rounded inline-flex items-center justify-center">c</span>
          CoreCRM
        </div>

     
        <div class="hidden md:flex space-x-6 text-(--emerald-dark) items-center">
          <a href="#" class="hover:text-(--emerald)">Features</a>
          <a href="#" class="hover:text-(--emerald)">Pricing</a>
          <a href="#" class="hover:text-(--emerald)">About</a>
          <a href="#" class="border bg-(--emerald) text-white px-6 rounded-2xl h-12 font-semibold flex items-center">Contact</a>
        </div>

        
        <button
          @click="toggleMenu"
          class="md:hidden text-gray-700 focus:outline-none"
        >
          <Menu />
        </button>
      </div>
    </div>

   
    <div v-if="isOpen" class="md:hidden px-4 pb-4 space-y-2 text-(--emerald-dark)">
      <a href="#" class="block hover:text-(--emerald)">Features</a>
      <a href="#" class="block hover:text-(--emerald)">Pricing</a>
      <a href="#" class="block hover:text-(--emerald)">About</a>
      <a href="#" class="block hover:text-(--emerald)">Contact</a>
    </div>
  </nav>
</template>


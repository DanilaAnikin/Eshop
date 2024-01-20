<script setup lang="ts">
import { MagnifyingGlassCircleIcon } from '@heroicons/vue/24/solid';
import { Bars3Icon, ShoppingCartIcon } from '@heroicons/vue/24/outline';
const searchInput = ref<string | null>(null);
</script>

<template>
    <div class="p-3 max-w-7xl gap-12 items-center">
        <div class="flex gap-8">
            <p class="text-3xl font-bold text-orange-600 font-serif cursor-pointer">ANAKYS</p>
            <div class="flex items-center gap-2 cursor-pointer">
                <h3>Categories</h3>
                <Bars3Icon class="h-6 w-6 mt-px" />
            </div>
        </div>

        <div class="flex border rounded-3xl border-black px-1">
            <input v-model="searchInput" type="text" class="rounded-l-3xl px-3 w-96 py-2 outline-none placeholder:text-slate-300 focus:placeholder:text-slate-200" placeholder="Search 4 NIGGS" >
            <MagnifyingGlassCircleIcon class="h-12 w-12 text-orange-500 cursor-pointer" />
        </div>
        
        <div class="flex gap-8">
            <p class="cursor-pointer hover:text-blue-900 font-serif">Sign in</p>
            <ShoppingCartIcon class="h-6 w-6 cursor-pointer" />
        </div>
    </div>
</template>
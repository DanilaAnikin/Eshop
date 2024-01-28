<script setup lang="ts">
import { MagnifyingGlassCircleIcon } from '@heroicons/vue/24/solid';
import { Bars3Icon, ShoppingCartIcon } from '@heroicons/vue/24/outline';

const searchInput = ref<string | null>(null);

</script>

<template>
    <div class="p-3 max-w-7xl gap-12 items-center">
        <div class="flex gap-8">
            <span class="text-3xl font-bold text-orange-600 font-serif cursor-pointer">ANAKYS</span>
            <div class="flex items-center gap-2 hover:text-slate-600 cursor-pointer">
                <span>Categories</span>
                <Bars3Icon class="h-6 w-6 mt-px" />
            </div>
        </div>

        <div class="flex border-[2px] rounded-3xl border-black px-1">
            <input v-model="searchInput" type="text" class="rounded-l-3xl px-3 w-96 py-2 outline-none placeholder:text-slate-400 focus:placeholder:text-slate-200" placeholder="Search 4 NIGGS" >
            <MagnifyingGlassCircleIcon class="h-12 w-12 text-orange-500 cursor-pointer hover:text-orange-600 transition-all duration-200" />
        </div>
        
        <div class="flex gap-6 items-center">
            <div @click="$emit('open-sign-in')" class="cursor-pointer hover:text-blue-900 font-serif rounded-2xl hover:bg-gray-100 transition-all duration-400 px-2 py-1">Sign in</div>
            <ShoppingCartIcon class="h-10 w-10 cursor-pointer mt-px rounded-3xl hover:bg-gray-100 transition-all duration-400 p-2" />
        </div>
    </div>
</template>

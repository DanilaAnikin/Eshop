<script setup lang="ts">
import Navbar from '../components/Navbar.vue';
import SignIn from '../components/SingIn.vue';
import { XMarkIcon } from '@heroicons/vue/24/outline';

const signInOpened = ref<boolean>(true);
</script>

<template>
    <div :class="`${ signInOpened ? 'opacity-30' : '' }`">
        <div class="w-full flex justify-center">
            <Navbar class="flex justify-center" @open-sign-in="signInOpened=true" />
        </div>
        <hr class="bg-slate-400 h-[2px]">
    </div>
    <div class="flex justify-center mt-40">
        <SignIn v-if="signInOpened" class="max-w-sm w-full" @close-popup="signInOpened=false" />
        <XMarkIcon v-if="signInOpened" @click="signInOpened=false" class="h-10 w-10 text-gray-800 cursor-pointer" />
    </div>
</template>

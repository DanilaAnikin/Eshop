<script setup lang="ts">
import { supabase } from '../src/supabase.js';
import dayjs from 'dayjs';

function iDontCare(message: string) {
    alert(message ? message : 'Unknown');
}

const haveAcc = ref<boolean>(true);

const emailInput = ref<string | null>('');
const passwordInput = ref<string | null>('');

async function createUser() {
    const userExist = await supabase.from('users').select().eq('email', emailInput.value);

    const { error } = await supabase.from('users').insert({
        email: emailInput.value,
        password: passwordInput.value,
        date: dayjs().format('YYYY,MM,DD'),
    });

    if(userExist.data?.length != 0) {
        alert('User already exist');
    } else {
        alert('Registered successfully');
    }
}

async function signIn() {
    const user = await supabase.from('users').select().eq('email', emailInput.value).eq('password', passwordInput.value);

    if(user.data?.length == 0) {
        alert('User does not exist');
    } else {
        alert('Logged in successfully!')
    }
}
</script>

<template>
    <div class="bg-gray-100 px-6 py-4 rounded-3xl gap-6 flex flex-col">
        <div class="flex justify-between items-center h-10">
                <span class="text-2xl font-semibold">Sign in</span>
                <span @click="haveAcc=!haveAcc" class="border-[2px] border-black rounded-3xl cursor-pointer py-[6px] px-3 font-semibold text-sm hover:border-orange-700 hover:bg-black hover:p-2 hover:text-slate-100 transition-all duration-800">Register</span>
            </div>
            <div class="flex flex-col gap-4">
                <label class="-mb-3 text-sm font-semibold" for="email">Email address</label>
                <input v-model="emailInput" type="email" placeholder="Your e-mail" class="rounded-lg px-2 py-2 h-12 font-mono">
                <label class="-mb-3 text-sm font-semibold" for="password">Password</label>
                <input v-model="passwordInput" type="password" placeholder="Your password" class="rounded-lg px-2 py-2 h-12 font-mono">
            </div>
            <span @click="iDontCare('I dont give a fuck :)')" class="text-sm hover:underline cursor-pointer">Forgot Your password?</span>
            <div @click="haveAcc ? signIn() : createUser()" class="text-slate-100 font-bold text-xl flex justify-center py-3 rounded-3xl bg-slate-900 w-full hover:bg-slate-950 cursor-pointer">
                Sign in
            </div>
        </div>
</template>
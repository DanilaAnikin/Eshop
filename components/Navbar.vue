<script setup lang="ts">
import type { DropdownItem } from '@nuxt/ui/dist/runtime/types';
const searchInput = ref<string | null>(null);
// interface Category {
//     label: string,
//     avatar?: {
//         src: string,
//     },
//     icon?: string,
//     shortcuts?: string[],
//     click?: () => {},
//     disabled?: boolean,
//     slot?: string
// }
const items = ref<DropdownItem[][]>([[{
    label: 'Kiss my ass',
    icon: 'i-heroicons-hand-thumb-up-circle-20-outline',
    shortcuts: ['⌘', 'K', 'M', 'A']
}], [{
    label: 'Delete',
    icon: 'i-heroicons-trash-20-solid',
    shortcuts: ['⌘', 'D']
}]]);

</script>

<template>
    <div class="p-3 max-w-7xl gap-12 items-center">
        <div class="flex gap-8">
            <span class="text-3xl font-bold text-orange-600 font-serif cursor-pointer">ANAKYS</span>
            <div class="flex items-center gap-2 hover:text-slate-600 cursor-pointer">
                <UDropdown :items="items" :popper="{ placement: 'bottom-start' }">
                    <UButton
                        color="orange"
                        label="Categories"
                        trailing-icon="i-heroicons-chevron-down-20-solid"
                    />
                </UDropdown>
            </div>
        </div>

        <UInput
            name="searchInput"
            icon="i-heroicons-magnifying-glass-20-solid"
            color="orange"
            variant="outline"
            placeholder="Search..."
            v-model="searchInput"
            autocomplete="off"
            :ui="{ icon: { trailing: { pointer: '' } } }"
        >
            <template #trailing>
                <UButton
                    v-show="searchInput !== ''"
                    color="gray"
                    variant="link"
                    icon="i-heroicons-x-mark-20-solid"
                    :padded="false"
                    @click="searchInput = ''"
                />
            </template>
        </UInput>
        <div class="flex gap-6 items-center">
            <div class="cursor-pointer hover:text-blue-900 font-serif rounded-2xl hover:bg-gray-100 transition-all duration-400 px-2 py-1">Sign in</div>
            <!-- <ShoppingCartIcon class="h-10 w-10 cursor-pointer mt-px rounded-3xl hover:bg-gray-100 transition-all duration-400 p-2" /> -->
            <UButton
                icon="i-heroicons-shopping-cart"
                size="sm"
                color="orange"
                square
                variant="outline"
            />
        </div>
    </div>
</template>

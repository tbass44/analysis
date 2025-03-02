<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Link, Head } from '@inertiajs/vue3';
import { reactive  } from 'vue';
import { Inertia } from "@inertiajs/inertia";
import { nl2br } from '@/common';

defineProps({
    item: Object,
})

</script>

<template>
    <Head title="商品登録" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">商品登録</h2>
        </template>

        <div class="py-8">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <section class="text-gray-600 body-font relative bg-white">
                    <div class="container px-5 py-12 mx-auto">
                        <div class="mx-auto">
                            <div class="flex flex-wrap -m-2">
                                <div class="p-2">
                                    <div class="relative">
                                        <label class="leading-7 text-sm text-gray-600">Name</label>
                                        <div class="w-full text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">{{ item.name }}</div>
                                    </div>
                                </div>
                                <div class="p-2 w-full">
                                    <div class="relative">
                                        <label for="memo" class="leading-7 text-sm text-gray-600">memo</label>
                                        <div v-html="nl2br(item.memo)" class="w-fulltext-base outline-none text-gray-700 py-1 px-3 resize-none leading-6 transition-colors duration-200 ease-in-out"></div>
                                    </div>
                                </div>
                                <div class="p-2 w-full">
                                    <div class="relative">
                                        <label class="leading-7 text-sm text-gray-600">price</label>
                                        <div class="w-fulltext-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">{{ item.price }}</div>
                                    </div>
                                </div>
                                <div class="p-2 w-full">
                                    <div class="relative">
                                        <label class="leading-7 text-sm text-gray-600">price</label>
                                        <div v-if="item.is_selling === 1" class="w-fulltext-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">販売中</div>
                                        <div v-if="item.is_selling === 0" class="w-fulltext-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out">停止中</div>
                                    </div>
                                </div>
                                <div class="p-2 w-full">
                                <Link as="button" :href="route('items.edit', { item: item.id })" class="flex mx-auto text-white bg-indigo-500 border-0 py-2 px-8 focus:outline-none hover:bg-indigo-600 rounded text-lg">編集する</Link>
                                </div>

                            </div>
                        </div>
                    </div>
                </section>
            </div>
        </div>
    </AuthenticatedLayout>
</template>

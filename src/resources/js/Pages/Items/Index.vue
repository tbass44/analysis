<script setup>
import AuthenticatedLayout from '@/Layouts/AuthenticatedLayout.vue';
import { Link, Head } from '@inertiajs/vue3';
import InertiaTest from '../InertiaTest.vue';
import FlashMessage from '@/Components/FlashMessage.vue'

defineProps({
    items: Array,
})
</script>

<template>
    <Head title="商品一覧" />

    <AuthenticatedLayout>
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">商品一覧</h2>
        </template>

        <div class="py-8">
            <FlashMessage />
            <section class="text-gray-600 body-font bg-white">
                <div class="container px-5 py-24 mx-auto">
                    <div class="lg:w-2/3 w-full mx-auto overflow-auto">
                    <table class="table-auto w-full text-left whitespace-no-wrap">
                        <thead>
                            <tr>
                            <th class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100 rounded-tl rounded-bl">Id</th>
                            <th class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100">商品名</th>
                            <th class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100">価格</th>
                            <th class="px-4 py-3 title-font tracking-wider font-medium text-gray-900 text-sm bg-gray-100">ステータス</th>

                            </tr>
                        </thead>
                        <tbody>
                            <tr v-for="item in items" :key="item.id">
                                <Link class="text-blue-400" :href="route('items.show', { item:
                                item.id })">
                                    {{ item.id }}
                                </Link>
                                <td>{{ item.name }}</td>
                                <td>{{ item.price }}</td>
                                <td>
                                    <span v-if="item.is_selling === 1">販売中</span>
                                    <span v-if="item.is_selling === 0 ">停止中</span>
                                </td>
                            </tr>
                        </tbody>
                    </table>
                    </div>
                    <div class="flex pl-4 mt-4 lg:w-2/3 w-full mx-auto">
                    <Link as="button" :href="route('items.create')" class="flex ml-auto text-white bg-indigo-500 border-0 py-2 px-6 focus:outline-none hover:bg-indigo-600 rounded">商品登録</Link>
                    </div>
                </div>
            </section>
        </div>
    </AuthenticatedLayout>
</template>

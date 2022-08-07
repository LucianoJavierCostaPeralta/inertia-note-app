<script setup>
import AppLayout from '@/Layouts/AppLayout.vue';
import { Link } from '@inertiajs/inertia-vue3';
defineProps({
    notes: Array
});

</script>

<template>
    <AppLayout title="Dashboard">
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Notes module
            </h2>
        </template>

        <div class="py-12">
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <div class="md:grid md:grid-cols-3 md:gap-6 ">
                    <div class="md:col-span-1 ">
                        <div class="px-4 sm:px-0">
                            <h3 class="text-lg text-gray-900">
                                Note list
                            </h3>
                            <p class="text-sm text-gray-600">
                                Take the correct record and run any function (view, edit, delete).
                            </p>
                        </div>
                    </div>
                    <div class="md:col-span-2 mt-5 md:mt-0">
                        <div class="shadow bg-white md:rounded-md p-4">
                            <table>
                                <tr v-for="note in notes" :key="note.id">
                                    <td class="border px-4 py-2">
                                        {{ note.excerpt}}
                                    </td>
                                    <td class="px-4 py-2 ">
                                        <Link class="view p-1 rounded-md " :href="route('notes.show', { id: note.id })">
                                            View
                                        </Link>
                                    </td>
                                    <td class="edit  px-4 py-2 ">
                                        <Link :href="route('notes.edit',note.id)">
                                        Edit
                                        </Link>
                                    </td>
                                </tr>
                            </table>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </AppLayout>
</template>

<style scoped>

    .edit{
        color: #1d5123;
    }
    .view {
        color: #ab2f9b;
    }

    .edit:hover, .view:hover {
        text-decoration: underline;
    }
</style>

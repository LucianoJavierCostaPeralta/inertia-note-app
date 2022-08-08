<script setup>
import AppLayout from '@/Layouts/AppLayout.vue';
import { Link, useForm } from '@inertiajs/inertia-vue3';

const form = useForm({
    excerpt: '',
    content:''
});

const submit = () => form.post(route('notes.store'), form);

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
                                Create note
                            </h3>
                            <p class="text-sm text-gray-600">
                                After creating, you will be able to edit the note.
                            </p>
                        </div>
                    </div>
                    <div class="md:col-span-2 mt-5 md:mt-0">
                        <div class="shadow bg-white md:rounded-md p-4">
                            <form @submit.prevent="submit">
                                <label class="block font-medium text-sm text-gray-700 my-2">
                                    Summary
                                </label>
                                <textarea
                                    class="form-input w-full rounded-md shadow-sm"
                                    v-model="form.excerpt"
                                ></textarea>
                                <label class="block font-medium text-sm text-gray-700 my-2">
                                    Content
                                </label>
                                <textarea
                                    class="form-input w-full rounded-md shadow-sm"
                                    v-model="form.content"
                                    rows="8"
                                ></textarea>
                                <button
                                    class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-md"
                                >Save</button>
                            </form>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </AppLayout>
</template>

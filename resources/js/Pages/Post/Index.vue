<template>

    <section class="bg-gray-50 dark:bg-gray-900 flex items-center">
    <div class="max-w-screen-xl px-4 mx-auto lg:px-12 w-full">
        <!-- Start coding here -->
        <div class="relative bg-white shadow-md dark:bg-gray-800 sm:rounded-lg">
        <div class="flex flex-col items-center justify-between p-4 space-y-3 md:flex-row md:space-y-0 md:space-x-4">
            <div class="w-full">
            <form class="flex">
                <div class="">
                <input type="text" disabled id="simple-search" class="block  p-2 pl-10 text-sm text-gray-900 border border-gray-300 rounded-lg bg-gray-50 focus:ring-primary-500 focus:border-primary-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-primary-500 dark:focus:border-primary-500" placeholder="Product" required="">
                </div>
                <Link href="posts/create" type="button" class="flex items-center justify-center px-4 py-2 text-sm font-medium text-white rounded-lg bg-primary-700 hover:bg-primary-800 focus:ring-4 focus:ring-primary-300 dark:bg-primary-600 dark:hover:bg-primary-700 focus:outline-none dark:focus:ring-primary-800">Add product   </Link>
            </form>
            </div>
        </div>
        </div>
    </div>
    </section>

    <div class="relative overflow-x-auto">
        <table class="w-full text-sm text-left rtl:text-right text-gray-500 dark:text-gray-400">
            <thead class="text-xs text-gray-700 uppercase bg-gray-50 dark:bg-gray-700 dark:text-gray-400">
                <tr>
                    <th v-for="header in headers" :key="header" scope="col" class="px-6 py-4">
                        {{ header }}
                    </th>
                </tr>
            </thead>
            <tbody>
                <tr class="bg-white border-b dark:bg-gray-800 dark:border-gray-700"  v-for="post in posts" :key="post.id">
                    <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">
                        {{ post.title }}
                    </th>
                    <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">
                        {{ post.title }}
                    </th>
                    <th scope="row" class="px-6 py-4 font-medium text-gray-900 whitespace-nowrap dark:text-white">
                        <Link as="button" :href="`posts/${post.id}/edit`">Edit</Link>&nbsp;
                        <button @click="deletePost(post.id)">Delete</button>
                    </th>
                </tr>
            </tbody>
        </table>
    </div>
</template>
<script setup>
import { Link, useForm } from "@inertiajs/vue3";

defineProps({
  posts: {
    type: Array,
    default: () => [],
  },
});

const headers = ["title", "body", "actions"];
const form = useForm({});
const deletePost = (id) => {
    form.delete(`posts/${id}`);
};
</script>

<template>
    <div class="justify-center m-5 grid ">
    <form @submit.prevent="submit" class="bg-white shadow-md rounded px-8 pt-6 pb-8 mb-4">
        <h1 class="text-2xl font-bold pl-3">Add product</h1>
        <div class="mb-4 pt-4">
            <label class="block text-gray-700 text-sm font-bold mb-2" for="username">
                Title
            </label>
            <input required class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" v-model="form.title"  type="text" placeholder="Title">
            </div>
            <div class="mb-6">
            <label class="block text-gray-700 text-sm font-bold mb-2" for="password">
                Body
            </label>
            <input required  v-model="form.body" class="shadow appearance-none border border-red-500 rounded w-full py-2 px-3 text-gray-700 mb-3 leading-tight focus:outline-none focus:shadow-outline"  type="text" placeholder="Body">
        </div>
        <div class="flex items-center justify-center">
        <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline" type="submit">
            Submit
        </button>
        </div>
    </form>
</div>
</template>
<script setup>
    import { onMounted } from "vue";
    import { useForm } from "@inertiajs/vue3";
    const props = defineProps({
        post: {
            type: Object,
            default: null,
        },
        isUpdating: {
            type: Boolean,
            default: false,
        },
    });
    const form = useForm({
        title: "",
        body: "",
    });
    const submit = () => (props.isUpdating ? updatePost() : addPost());
    const addPost = () => form.post("/posts");
    const updatePost = () => form.put(`/posts/${props.post.id}`);
    onMounted(() => {
        form.title = props.post?.title;
        form.body = props.post?.body;
    });
  </script>
  <style lang="scss" scoped></style>

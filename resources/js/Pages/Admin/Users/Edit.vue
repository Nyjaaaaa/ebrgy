<template>
    <AdminLayout title="Update user">
        <template #header>
            <h2 class="font-semibold text-xl text-gray-800 leading-tight">
                Update User
            </h2>
        </template>

        <div>
            <div class="max-w-7xl mx-auto sm:px-6 lg:px-8">
                <section class="container mx-auto p-6">
                    <div
                        class="w-full mb-8 overflow-hidden rounded-lg shadow-lg"
                    >
                        <div class="w-full shadow p-5 bg-gray-800">
                            <form @submit.prevent="updateUser">
                                <div class="relative z-0 w-full mb-6 group">
                                    <input
                                        v-model="form.name"
                                        type="name"
                                        name="name"
                                        id="name"
                                        class="block py-2.5 px-0 w-full text-sm text-gray-900 bg-transparent border-0 border-b-2 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-blue-500 focus:outline-none focus:ring-0 focus:border-blue-600 peer"
                                        placeholder=" "
                                    />
                                    <div
                                        v-if="errors.name"
                                        class="text-red-600"
                                    >
                                        {{ errors.name }}
                                    </div>
                                    <label
                                        for="name"
                                        class="peer-focus:font-medium absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-6 scale-75 top-3 -z-10 origin-[0] peer-focus:left-0 peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-6"
                                        >Full name</label
                                    >
                                    
                                </div>
                                <div class="relative z-0 w-full mb-6 group">
                                    <input
                                        v-model="form.email"
                                        type="email"
                                        name="email"
                                        id="email"
                                        class="block py-2.5 px-0 w-full text-sm text-gray-900 bg-transparent border-0 border-b-2 border-gray-300 appearance-none dark:text-white dark:border-gray-600 dark:focus:border-blue-500 focus:outline-none focus:ring-0 focus:border-blue-600 peer"
                                        placeholder=" "
                                    />
                                    <label
                                        for="email"
                                        class="peer-focus:font-medium absolute text-sm text-gray-500 dark:text-gray-400 duration-300 transform -translate-y-6 scale-75 top-3 -z-10 origin-[0] peer-focus:left-0 peer-focus:text-blue-600 peer-focus:dark:text-blue-500 peer-placeholder-shown:scale-100 peer-placeholder-shown:translate-y-0 peer-focus:scale-75 peer-focus:-translate-y-6"
                                        >Email address</label
                                    >
                                    <div
                                        v-if="errors.email"
                                        class="text-red-600"
                                    >
                                        {{ errors.email }}
                                    </div>
                                </div>
                                <button
                                    :disabled="form.processing"
                                    type="submit"
                                    class="text-gray-900 bg-white hover:bg-blue-100 border border-blue-200 font-medium rounded-lg text-sm px-5 py-2.5 text-center inline-flex items-center dark:focus:ring-blue-600 dark:bg-blue-800 dark:border-blue-700 dark:text-white dark:hover:bg-blue-700 m-4"
                                >
                                    Submit
                                </button>
                                <Link
                                    :href="route('admin.users.index')"
                                    class="text-gray-900 bg-white hover:bg-red-100 border border-red-200 font-medium rounded-lg text-sm px-5 py-2.5 text-center inline-flex items-center dark:focus:ring-red-600 dark:bg-red-800 dark:border-red-700 dark:text-white dark:hover:bg-red-700 m-4"
                                    ><span>Cancel</span>
                                </Link>
                            </form>
                        </div>
                    </div>
                </section>
            </div>
        </div>
    </AdminLayout>
</template>

<script setup>
import AdminLayout from "@/Layouts/AdminLayout.vue";
import { Link, useForm } from "@inertiajs/inertia-vue3";
import { defineProps } from "vue";

const props = defineProps({
    user: Object,
    errors: Object,
});

const form = useForm({
    id: props.user.id,
    name: props.user.name,
    email: props.user.email,
});

function updateUser() {
    form.put(route("admin.users.update", form.id));
}
</script>

<script setup>
import { Head, Link } from "@inertiajs/vue3";

defineProps({
    canLogin: {
        type: Boolean,
    },
    canRegister: {
        type: Boolean,
    },
    laravelVersion: {
        type: String,
        required: true,
    },
    phpVersion: {
        type: String,
        required: true,
    },
});
</script>

<template>
    <Head title="Welcome" />
    <div class="h-screen w-screen bg-[#ff71ce]">
        <div
            v-if="canLogin"
            class="w-full sm:fixed sm:top-0 sm:right-0 py-2 px-8 text-right bg-yellow-200 flex items-center justify-between"
        >
            <div class="h-8 aspect-square mb-2">
                <img
                    src="https://cdn.discordapp.com/attachments/1069729310262435860/1128575497291448410/myLogo.svg"
                    alt="iniLogo"
                />
            </div>

            <Link
                v-if="$page.props.auth.user"
                :href="route('dashboard')"
                class="font-semibold text-gray-600 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white focus:outline focus:outline-2 focus:rounded-sm focus:outline-red-500"
                >Dashboard</Link
            >

            <div v-else>
                <Link
                    :href="route('login')"
                    class="font-semibold text-gray-600 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white focus:outline focus:outline-2 focus:rounded-sm focus:outline-red-500"
                    >Log in</Link
                >

                <Link
                    v-if="canRegister"
                    :href="route('register')"
                    class="ml-4 font-semibold text-gray-600 hover:text-gray-900 dark:text-gray-400 dark:hover:text-white focus:outline focus:outline-2 focus:rounded-sm focus:outline-red-500"
                    >Register</Link
                >
            </div>
        </div>
        <main class="h-full w-full flex items-center justify-center">
            <div class="h-full w-1/2 flex flex-col items-center justify-center">
                <div
                    class="h-auto w-1/2 flex flex-col items-start justify-center gap-4"
                >
                    <h1 class="text-4xl font-extrabold">Lorem, ipsum.</h1>
                    <h2 class="text-xl">
                        Lorem ipsum dolor sit amet consectetur adipisicing elit.
                        Culpa eos rerum quo. Aut ducimus cum cupiditate atque
                        voluptatum in nostrum nam. Provident, quisquam? Ratione.
                    </h2>
                    <Link
                        v-if="$page.props.auth.user"
                        :href="route('dashboard')"
                        class="p-2 bg-yellow-200 rounded-md"
                        >Go to Dasboard</Link
                    >
                    <div v-else class="flex items-center justify-center gap-2">
                        <Link
                            :href="route('login')"
                            class="p-2 bg-yellow-200 rounded-md"
                            >Login</Link
                        >
                        <Link
                            :href="route('register')"
                            class="p-2 bg-yellow-200 rounded-md"
                            >Register</Link
                        >
                    </div>
                </div>
            </div>
            <div class="h-full w-1/2 flex flex-col items-center justify-center">
                <img
                    src="https://cdn.discordapp.com/attachments/1069940642521825320/1070416722126962808/pepocorn-eat.gif"
                    alt="gif"
                    class="h-1/2 aspect-square"
                />
            </div>
        </main>
    </div>
</template>

<style>
.bg-dots-darker {
    background-image: url("data:image/svg+xml,%3Csvg width='30' height='30' viewBox='0 0 30 30' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M1.22676 0C1.91374 0 2.45351 0.539773 2.45351 1.22676C2.45351 1.91374 1.91374 2.45351 1.22676 2.45351C0.539773 2.45351 0 1.91374 0 1.22676C0 0.539773 0.539773 0 1.22676 0Z' fill='rgba(0,0,0,0.07)'/%3E%3C/svg%3E");
}
@media (prefers-color-scheme: dark) {
    .dark\:bg-dots-lighter {
        background-image: url("data:image/svg+xml,%3Csvg width='30' height='30' viewBox='0 0 30 30' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M1.22676 0C1.91374 0 2.45351 0.539773 2.45351 1.22676C2.45351 1.91374 1.91374 2.45351 1.22676 2.45351C0.539773 2.45351 0 1.91374 0 1.22676C0 0.539773 0.539773 0 1.22676 0Z' fill='rgba(255,255,255,0.07)'/%3E%3C/svg%3E");
    }
}
</style>

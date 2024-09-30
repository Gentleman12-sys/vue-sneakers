<script setup>
const emit = defineEmits(['toggleDrawer']);
</script>


<template>
    <header class="flex justify-between border-b border-slate-300 px-4">
        <div class="flex items-center gap-2">
            <img class="w-16 mt-4"
                src="https://d1csarkz8obe9u.cloudfront.net/posterpreviews/sneaker-store-logo-brand-logo-design-template-ea9c8040d69fa064feee3014cb8e9827_screen.jpg?ts=1645976739https://d1csarkz8obe9u.cloudfront.net/posterpreviews/sneaker-store-logo-brand-logo-design-template-ea9c8040d69fa064feee3014cb8e9827_screen.jpg?ts=1645976739"
                alt="logo">
            <div>
                <h2 class="text-xl font-bold uppercase">Vue Sneakers</h2>
                <p class="text-slate-500">Магазин кросовок</p>
            </div>
        </div>
        <ul class="flex items-center gap-5">
            <li @click="() => emit('toggleDrawer', true)" class="text-gray-500 cursor-pointer hover:text-black transition duration-150">Корзина</li>
            <li class="text-gray-500 cursor-pointer hover:text-black transition duration-150">Закладки</li>
            <li class="text-gray-500 cursor-pointer hover:text-black transition duration-150">Профиль</li>
        </ul>
    </header>
</template>
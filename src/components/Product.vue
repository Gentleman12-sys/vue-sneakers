<script setup>
defineProps({
    title: String,
    price: Number,
    imgUrl: String,
    inCart: Boolean
});
const emit = defineEmits(['onClickCart']);
</script>

<template>
    <div>
        <div @click="() => emit('onClickCart', $props)" class="relative w-fit border border-slate-200 rounded-3xl p-8 cursor-pointer hover:-translate-y-2 hover:shadow-xl transition duration-150">
            <img class="w-64" :src="imgUrl" alt="sneakers">
            <p class="mt-4">{{ title }}</p>
            
            <div class="flex justify-between mt-1">
                <div class="flex flex-col">
                    <span class="text-slate-400">Цена:</span>
                    <b>{{ price }} ₽</b>
                </div>
            </div>
        </div>
    </div>
</template>
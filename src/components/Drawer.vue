<script setup>
const emit = defineEmits(['toggleDrawer']);
</script>


<template>
    <div>
        <div @click="() => emit('toggleDrawer', false)" class="fixed top-0 left-0 w-full h-full bg-black z-10 opacity-70"></div>
        <div class="bg-white w-96 h-full fixed right-0 top-0 z-20 p-8 rounded-l-xl"></div>
    </div>
</template>
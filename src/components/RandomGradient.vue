<template>
    <div><div class="grid mx-auto place-items-center">
        <h2 class="my-5 text-xl font-bold">Random Gradient</h2>
        <button class="p-2 my-4 border-2 border-slate-800 w-100 hover:bg-pink-200" @click="RandomGradient">Random Color</button></div>
        <div class="gradient" :style="`background: linear-gradient(${Math.random()*360}deg,#${color1},#${color2})`"></div>
    </div>
</template>

<script lang="ts">
    export default {
        name:"RandomGradient",
        data() {
            return {
                color1: Math.floor(Math.random()*16777215).toString(16),
                color2: Math.floor(Math.random()*16777215).toString(16),
            }
        },
        methods: {
            RandomGradient() {
                this.color1 = Math.floor(Math.random()*16777215).toString(16);
                this.color2 = Math.floor(Math.random()*16777215).toString(16);
            }
        },
    }
</script>

<style scoped>
.gradient{
    height: calc(100vh - 100px);
}
</style>
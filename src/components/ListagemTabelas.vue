<script setup>
</script>


<template>
    <div>
        <h1>Administração do Site</h1>
        <div class="container">
            <div class="card" v-for="produto in produtos" :key="produto.id">
            </div>
        </div>
    </div>
</template>
<style scoped>
h1{
    color: rgb(255, 255, 255);
    font-family: "Segoe UI", system-ui, Roboto, "Helvetica Neue", Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
    font-size: 16px
}
</style>
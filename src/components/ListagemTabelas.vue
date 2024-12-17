<script setup>
</script>
<template>
    <div>
        <h1>Administração do Site</h1>
        <div class="container">
        </div>
        <div class="table">
            <!-- <router-link to="/usuarios">Usuários</router-link> -->
            <!-- <router-link to="/categorias">Categorias</router-link> -->
            <button>
                <router-link :to="{ name: 'Produtos' }" class="back">
                    <div class="back">
                        Voltar
                    </div>
                </router-link>
            </button>
            <!-- <router-link to="/pedidos">Pedidos</router-link> -->
        </div>
    </div>
</template>
<style scoped>
h1 {
    color: rgb(255, 255, 255);
    font-family: "Segoe UI", system-ui, Roboto, "Helvetica Neue", Arial, sans-serif, "Apple Color Emoji", "Segoe UI Emoji", "Segoe UI Symbol", "Noto Color Emoji";
    font-size: 16px;
    text-align: center;
}

.table {
    background-color: white;
}
</style>
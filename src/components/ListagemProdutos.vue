<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';
const produtos = ref([]);

onMounted(async () => {
    const response = await axios.get('https://fakestoreapi.com/products');
    produtos.value = response.data;
});

const formatPrice = (price) => `R$ ${price.toFixed(2).replace('.', ',')}`;
</script>


<template>
    <div>
        <h1>Produtos</h1>
        <div class="container">
            <div class="card" v-for="produto in produtos" :key="produto.id">
                <h1 class="card--title">{{ produto.title }}</h1>
                <p>{{ produto.description }}</p>
                <p>{{ formatPrice(produto.price) }}</p>
                <img class="card--avatar" :src="produto.image" :alt="produto.title" />
            </div>
        </div>
    </div>
</template>
<style scoped>
.container {
    gap: 0.5rem;
}

.card {
    width: 92%;
}

@media (min-width: 768px) and (max-width: 1024px) {
    .card {
        width: 22rem;
    }
}

.card--avatar {
    width: 100%;
    height: 17rem;
    object-fit: cover;
    margin-bottom: 0.5rem;
}

.card--title {
    color: #222;
    font-weight: 700;
    text-transform: capitalize;
    font-size: 1.1rem;
    margin-top: 0.5rem;
}
</style>
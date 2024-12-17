<script setup>
import ListagemProdutos from '@/components/ListagemProdutos.vue';
</script>
<template>
    <div>
        <h2>Nossos Produtos:</h2>
        <ListagemProdutos/>
    </div>
</template>

<style scoped>
h2{
    text-align: center;
}
.back {
    text-decoration: none;
    color: #ffffff;
    font-weight: bold;
    text-decoration-line: none;
}
button{
    margin-top: 20px;
    padding: 10px 20px;
    background-color: #000000;
    color: #fff;
    border: none;
    cursor: pointer;
    transition: background-color 0.3s ease;
    border-radius: 7px;

}
.back{
    text-decoration: none;
    color: #ffffff;
    align-items: center;
    display: flex;
    justify-content: center;
    font-weight: bold;
    font-size: 15px;
    background-color: #000000;
    color: #fff;
    border: none;
    cursor: pointer;

}
</style>
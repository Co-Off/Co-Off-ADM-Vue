<script setup>
import { ref, onMounted, watch } from 'vue';
import { useProdutoStore } from '@/stores/produto';
import ModalSpamProduto from './ModalSpamProduto.vue'
import { formatPrice } from '@/helpers/format';

const props = defineProps(['categoria_id']);
const produtoStore = useProdutoStore(); 
const showSpamProduct = ref(false)
const currentProduct = ref({})

async function getProdutos() {
  if (props.categoria_id) {
    await produtoStore.getProdutosPorCategoria(props.categoria_id);
  } else {
    await produtoStore.getProdutos();
  }
}

function showProduct(produto) {
  currentProduct.value = produto
  showSpamProduct.value = true
}

watch(
  () => props.categoria_id,
  async () => {
    await getProdutos();
  },
);

onMounted(async () => {
  await getProdutos();
  console.log(produtoStore.produtos)
});
</script>

<template>
  
  <div class="produto-list">
    <div v-if="produtoStore.produtos.length === 0">
      <h3 class="spam">Produtos não encontrados!</h3>
    </div>
    <div
      v-for="produto in produtoStore.produtos"
      :key="produto.id"
      class="cards"
    >
        <div @click="showProduct(produto)">
          <div class="produto-img-wrapper">
            <img :src="produto.imagemDoProduto?.url" alt="produto.image" />
            <i class="mdi mdi-heart-outline" />
          </div>
          <div class="produto-title-price">
            <p>{{ produto.nome }}</p>
            <p>{{ formatPrice(produto.preco * 1) }}</p>
          </div>
          <div class="produto-description-stars">
          </div>
        </div>
    </div>
  </div>
  <ModalSpamProduto v-if="showSpamProduto" @close="showSpamProduto=false" :product="currentProduct" />
</template>

<style scoped>
.cards{
  width: 200px;
  height: 300px;

  overflow: hidden;
  position: relative;

  border: solid;
  border-radius: 20px;
   border-width: 0.15em;
}
.cards:hover {
  transform: scale(1.1,1.1);
  transition-delay: 0.1s;
  transition: 0.4s;
}

.cards:hover > .cards:not(:hover) {
  filter: blur(10px);
  transform: scale(0.9, 0.9);
}

.icon {
  background-color: #000000;
  color: white;
  border: none;
  border-radius: 50%;
  width: 50px;
  height: 50px;

  position: fixed;
  bottom: 12rem;
  right: 20px;
}

.icon:hover {
  background-color: #bac9e8;
  color: #0a2668;
}

.icon i {
  font-size: 2rem;
}

.produto-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  padding: 1rem;
  gap: 2rem;
  text-align: center;
  background-color: #ffffff;
  
}

.produto-card {
  width: 200px;
  font-family: 'Belleza', sans-serif;
  border: #000000;
}

.produto-img-wrapper {
  display: flex;
  justify-content: center;
  align-items: top;
  padding-top: 20px;
  background-color: #ffffff;
  height: 200px;
}

.produto-img-wrapper img {
  width: 153px;
  height: 170px;
  object-fit: cover;
}

.produto-title-price {
  display: flex;
  flex-direction: column;
  justify-content: space-evenly;
  align-items: center;
  margin: 3px;
}

.produto-title-price p {
  font-weight: bold;
  font-size: 16px;
  color: #010101;
}

.produto-description-stars {
  display: flex;
  flex-direction: column;
  margin-bottom: 1rem;
}

.produto-description-stars p {
  font-size: 12px;
  color: #535050;
}

</style>
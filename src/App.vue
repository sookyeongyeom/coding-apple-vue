<template>
  <transition name="fade">
    <Modal :selected-product="selectedProduct" :products="products" @unselectProduct="unselectProduct" />
  </transition>
  <Menu />
  <Discount />
  <button @click="priceSortByAsc">저렴한순정렬</button>
  <button @click="priceSortByDesc">비싼순정렬</button>
  <button @click="resetSort">되돌리기</button>
  <Card v-for="(product, i) in products" :key="i" :product="product" @selectProduct="() => selectProduct(i)" />
</template>

<script>
import { onerooms } from './mocks';
import { Discount, Modal, Card, Menu } from './components';

export default {
  name: 'App',
  components: { Discount, Modal, Card, Menu },
  data() {
    return {
      selectedProduct: -1,
      products: onerooms,
      productsOrg: [...onerooms],
    };
  },
  methods: {
    selectProduct(idx) {
      this.selectedProduct = idx;
    },
    unselectProduct() {
      this.selectedProduct = -1;
    },
    priceSortByAsc() {
      this.products.sort((a, b) => a.price - b.price);
    },
    priceSortByDesc() {
      this.products.sort((a, b) => b.price - a.price);
    },
    resetSort() {
      this.products = [...this.productsOrg];
    },
  },
};
</script>

<style>
body {
  margin: 0;
}

* {
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.fade-enter-from {
  opacity: 0;
}

.fade-enter-active {
  transition: 0.3s ease;
}

.fade-enter-to {
  opacity: 1;
}

.fade-leave-from {
  opacity: 1;
}

.fade-leave-active {
  transition: 0.3s ease;
}

.fade-leave-to {
  opacity: 0;
}
</style>

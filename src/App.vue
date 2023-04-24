<template>
  <div v-if="selectedProduct !== -1" @click="unselectProduct" class="black-bg">
    <div @click="stopPropagation" class="white-bg">
      <img :src="products[selectedProduct].image" />
      <h4>{{ products[selectedProduct].title }}</h4>
      <p>{{ products[selectedProduct].content }}</p>
      <p>{{ products[selectedProduct].price }}원</p>
    </div>
  </div>
  <div class="menu">
    <a v-for="menu in menus" :key="menu">{{ menu }}</a>
  </div>
  <div v-for="(product, i) in products" :key="i" class="product">
    <img :src="product.image" />
    <h4 @click="() => selectProduct(i)">{{ product.title }}</h4>
    <p>{{ product.price }}원</p>
  </div>
</template>

<script>
import { onerooms } from './mocks/onerooms';

export default {
  name: 'App',
  data() {
    return {
      // price1: 60,
      // price2: 70,
      // price3: 80,
      // products: [
      //   { name: '역삼동원룸', price: 60, reportCnt: 0 },
      //   { name: '천호동원룸', price: 70, reportCnt: 0 },
      //   { name: '마포구원룸', price: 80, reportCnt: 0 },
      // ],
      menus: ['Home', 'Products', 'About'],
      selectedProduct: -1,
      products: onerooms,
    };
  },
  methods: {
    // increaseReportCnt(idx) {
    //   this.products[idx].reportCnt++;
    // },
    // showModal() {
    //   this.isShowModal = true;
    // },
    // hideModal() {
    //   this.isShowModal = false;
    // },
    selectProduct(idx) {
      this.selectedProduct = idx;
    },
    unselectProduct() {
      this.selectedProduct = -1;
    },
    stopPropagation(event) {
      event.stopPropagation();
    },
  },
  components: {},
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

.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}

.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}

.white-bg img {
  width: 100%;
}

.menu {
  background: darkslateblue;
  padding: 15px;
}

.menu a {
  color: white;
  padding: 10px;
}

.product h4 {
  cursor: pointer;
}

.product img {
  width: 100%;
  margin-top: 40px;
}
</style>

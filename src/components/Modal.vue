<template>
  <div v-if="selectedProduct !== -1" class="black-bg" @click="$emit('unselectProduct')">
    <div class="white-bg" @click="stopPropagation">
      <img :src="products[selectedProduct].image" />
      <h4>{{ products[selectedProduct].title }}</h4>
      <p>{{ products[selectedProduct].content }}</p>
      <p>{{ products[selectedProduct].price }}원</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Modal',
  props: {
    selectedProduct: {
      type: Number,
      default: function () {
        return -1;
      },
    },
    products: {
      type: Array,
      default: function () {
        return [];
      },
    },
  },
  emits: ['unselectProduct'],
  methods: {
    stopPropagation(event) {
      event.stopPropagation();
    },
  },
};
</script>

<style>
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
</style>

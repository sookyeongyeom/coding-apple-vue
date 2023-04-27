<template>
  <div class="product">
    <img :src="product.image" />
    <h4 @click="$emit('selectProduct')">
      {{ product.title }}
    </h4>
    <p>{{ product.price }}원</p>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    product: {
      type: Object,
      default: function () {
        return {};
      },
    },
  },
  emits: ['selectProduct'],
};
</script>

<style>
.product h4 {
  cursor: pointer;
}

.product img {
  width: 100%;
  margin-top: 40px;
}
</style>

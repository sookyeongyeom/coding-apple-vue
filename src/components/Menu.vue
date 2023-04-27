<template>
  <div class="menu">
    <a v-for="menu in menus" :key="menu">{{ menu }}</a>
  </div>
</template>

<script>
export default {
  name: 'Menu',
  data() {
    return {
      menus: ['Home', 'Products', 'About'],
    };
  },
};
</script>

<style>
.menu {
  background: darkslateblue;
  padding: 15px;
}

.menu a {
  color: white;
  padding: 10px;
}
</style>

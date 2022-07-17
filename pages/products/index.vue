<template>
  <div>
    <h1>Products</h1>
    <ul>
      <li v-for="item in products" :key="item.id">
        <nuxt-link :to="'/products/' + item.id">{{ item.title }}</nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      products: [],
    };
  },
  async asyncData() {
    const res = await fetch(
      "https://6204eefd161670001741b078.mockapi.io/api/v1/products"
    );
    const products = await res.json();
    return { products };
  },
}
</script>

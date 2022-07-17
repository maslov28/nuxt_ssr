<template>
<div>
  <h1>Item</h1>
  <h3>{{product.title}}</h3>
  <p>{{product.description}}</p>
  <span>{{product.price}}</span>

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
  computed: {
    product() {
      return this.products.find(el => el.id === this.$route.params.id)
    }
  }
}
</script>
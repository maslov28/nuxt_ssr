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
  async asyncData({params}) {
    const res = await fetch(
      `https://6204eefd161670001741b078.mockapi.io/api/v1/products/${params.id}`
    );
    const product = await res.json();
    return { product };
  },
  computed: {
    id() {
      return this.$route.params.id
    }
  }
}
</script>
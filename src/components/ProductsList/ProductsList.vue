<template>
  <div  class="list">
    <ProductItem 
      v-for="product in products"
      :key="product.id"
      :product="product"
      :setCount="setCount"
    />
  </div>
</template>

<script>
import ProductItem from "./ProductItem/ProductItem.vue";

export default {
  name: "ProductsList",
  components: {
    ProductItem
  },
  props: ["products", "setCount"],
}
</script>

<style scoped>
.list {
  display: flex;
  flex-wrap: wrap;
  align-items: stretch;
  align-content: flex-start;
}
</style>

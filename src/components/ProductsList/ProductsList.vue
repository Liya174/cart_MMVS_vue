<template>
  <div>
    <ProductItem v-for="product in products" :key="product.id" :product="product" />
  </div>
</template>

<script>
import ProductItem from './ProductItem/ProductItem.vue';

export default {
  name: 'ProductsList',
  components: {
    ProductItem
  },
  data() {
    return { 
      products: [
        {
          id: 0,
          title: 'Item1',
          price: 40,
        },
        {
          id: 1,
          title: 'Item2',
          price: 10
        },
      ]
    }
  }
}
</script>

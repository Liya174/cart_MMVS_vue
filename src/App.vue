<template>
  <div class="container">
    <ProductsList :products="products" :setCount="setCount"/>
    <UserOrder :products="products" :onOrderButtonClick="toggleModalOpen" />
    <OrderModal v-if="isModalOpen" :products="products" :onOkButtonClick="toggleModalOpen"/>
  </div>
</template>

<script>
import OrderModal from "./components/OrderModal/OrderModal.vue"
import ProductsList from "./components/ProductsList/ProductsList.vue"
import UserOrder from "./components/UserOrder/UserOrder.vue"
import { fakeData } from "../public/fakes/Fakes";

export default {
  name: "App",
  components: {
    ProductsList,
    UserOrder,
    OrderModal
  },
  data() {
    return {
      isModalOpen: false,
      products: fakeData.map(data => {
        return {
          ...data,
          count: 0
        }
      })
    }
  },
  methods: {
    setCount(newCount, id) {
      const newData = this.products.map(product => {
        if (product.id === id) {
          return {
            ...product,
            count: newCount
          }
        }
        return product; 
      })

      this.products = newData;
    },
    toggleModalOpen() {
      this.isModalOpen = !this.isModalOpen;
    }
  }
}
</script>

<style scoped>
* {
  box-sizing: border-box;
  margin: 0;
}

p {
  padding-bottom: 15px;
}

.container {
  display: grid;
  grid-template-columns: 1fr 250px;
  grid-column-gap: 10px;
  max-width: 1200px;
  min-height: 100vh;
  width: 95%;
  margin: 0 auto;
}
</style>

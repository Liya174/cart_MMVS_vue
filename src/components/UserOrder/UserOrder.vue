<template>
  <div class="sidebar">
    <div>Ваш заказ:</div>
    
    <OrderList v-if="hasProducts" :products="products" />
    <div v-else>Пусто</div>
    
    <OrderButton 
      :products="products"
      :onClick="onOrderButtonClick"
    />
  </div>
</template>

<script>
import OrderList from "./OrderList/OrderList.vue";
import OrderButton from "./OrderButton/OrderButton.vue"

export default {
  name: "UserOrder",
  components: {
    OrderList,
    OrderButton
  },
  props: ["products", "onOrderButtonClick"],
  computed: {
    hasProducts() {
      return this.products.reduce((prevValue, currentValue) => prevValue.count + currentValue.count, 0) > 0;
    }
  }
}
</script>

<style scoped>
.sidebar {
  display: flex;
  flex-direction: column;
  padding: 20px;
  background-color: rgba(134, 76, 125, 0.2);
}
</style>

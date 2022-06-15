<template>
  <div class="sidebar">
    <div>Ваш заказ:</div>
    
    <OrderList v-if="hasProducts" :products="orderProducts" />
    <div v-else>Пусто</div>
    
    <OrderButton 
      :products="orderProducts"
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
      return this.products.reduce((accumulator, currentValue) => +accumulator + +currentValue.count, 0) > 0;
    },
    orderProducts() {
      return this.products.filter(product => product.count > 0);
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

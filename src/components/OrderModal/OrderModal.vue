<template>
  <div class="modal">
      <div class="content">
        <p>Общая стоимость заказа: {{ sum }} руб.</p>
        <button @click="onOkButtonClick">Ok</button>
    </div>
  </div>
</template>
<script>

export default {
  name: "OrderModal",
  props: ["products", "onOkButtonClick"],
  computed: {
    sum() {
      return this.products
        .map(product => +product.price * +product.count )
        .reduce((prevValue, currentValue) => prevValue + currentValue, 0);
    }
  }
}
</script>

<style scoped>
.modal {
    position: fixed;
    z-index: 1;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0,0,0,0.4);
}

.content {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    background-color: #fefefe;
    margin: 20% auto;
    padding: 20px;
    border: 1px solid #888;
    width: 50%;
}
</style>

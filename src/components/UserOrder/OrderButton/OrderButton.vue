<template>
  <button 
    class="button"
    :disabled="isDisabled"
  >
    Заказать
  </button>
</template>

<script>

export default {
  name: "OrderButton",
  props: ["products", "count"],
  computed: {
    isDisabled() {
      return this.products.reduce((accumulator, currentValue) => +accumulator + +currentValue.count, 0) === 0;
    }
  }
}
</script>

<style scoped>
.button {
  margin-top: 20px;
}
</style>

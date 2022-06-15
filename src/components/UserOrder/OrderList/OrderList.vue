<template>
  <ul>
    <li 
      v-for="product in products" 
      :key="product.id"
    >
      <span>{{ product.title }}</span>
      <span v-if="product.count > 1">&nbsp;({{ product.count }})</span>
    </li>
  </ul>
</template>

<script>

export default {
  name: "OrderList",
  props: ["products"],
}
</script>
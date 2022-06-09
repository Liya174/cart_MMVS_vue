<template>
  <div>
    it's {{ product.title }}. it costs {{ product.price }}
  </div>
</template>

<script>
export default {
  props: {
    product: Object,
  }
}
</script>

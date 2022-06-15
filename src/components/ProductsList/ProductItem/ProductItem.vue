<template>
  <div class="container" :class="{ active: product.count > 0 }">
    <img :src="product.imgUrl" :alt="product.title" class="image" />
    <p>{{ product.title }}</p>
    <p>{{ product.description }}</p>

    <div class="itemFooter">
      <p>Цена: {{ product.price }} руб.</p>   

      <button v-if="product.count === 0" class="itemButton" @click="() => changeCount('add')">
        Добавить в корзину
      </button>

      <div v-else class="counterContainer">
        <button 
          class="itemButton"
          @click="() => changeCount('remove')"
        >
          -
        </button>
        <div class="counter">{{ product.count }}</div>
        <button 
          class="itemButton"
          @click="() => changeCount('add')"
        >
          +
        </button>
      </div>
    </div>

  </div>
</template>

<script>
const MIN_PRODUCTS_COUNT = 0;
const MAX_PRODUCTS_COUNT = 99;

export default {
  props: ["product", "setCount"],
  methods: {
    changeCount(value) {
      let newCount = this.product.count;

      if (value === "add") newCount++; 
      if (value === "remove") newCount--;

      if (newCount <= MAX_PRODUCTS_COUNT && newCount >= MIN_PRODUCTS_COUNT) {
        return this.setCount(newCount, this.product.id)
      }
    }
  }
}
</script>

<style scoped>
.container {
  width: 200px;
  margin: 10px;
  padding: 10px;
  display: flex;
  flex-direction: column;
  align-items: center;
  border: 2px solid rgb(223, 223, 223);
}

.container.active {
  border-color: green;
}

.itemFooter {
  width: 100%;
  margin-top: auto;
  text-align: center;
}

.itemButton {
  width: 100%;
  cursor: pointer;
}

.counterContainer {
  width: 100%;
  display: grid;
  grid-template-columns: repeat(3, 1fr);
}

.counter {
  text-align: center;
}

.image {
  width: 100%;
  height: 150px;
  object-fit: contain;
}
</style>

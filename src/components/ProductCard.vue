<script>
import QuantitySelector from './QuantitySelector.vue'

export default {
  name: 'ProductCard',
  components: { QuantitySelector },
  props: {
    product: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      quantity: 1,
    }
  },
  methods: {
    onQuantityChange(value) {
      this.quantity = value
    },
    addToCart() {
      this.$emit('add-to-cart', {
        ...this.product,
        quantity: this.quantity,
      })
    },
  },
}
</script>

<template>
  <article class="card">
    <img class="image" :src="product.image" :alt="product.title" />
    <div class="body">
      <h3 class="title">{{ product.title }}</h3>
      <p class="description">{{ product.description }}</p>
      <div class="meta">
        <p class="price">{{ product.price }} BYN</p>
        <span class="rating">
          <img class="star" src="../assets/star.svg" alt="" />
          {{ product.rating }}
        </span>
      </div>
      <QuantitySelector @change="onQuantityChange" />
      <button type="button" class="button" @click="addToCart">
        <img class="icon" src="../assets/cart1.svg" alt="" />
        В корзину
      </button>
    </div>
  </article>
</template>

<style scoped>
.card {
  display: flex;
  flex-direction: column;
  width: 320px;
  overflow: hidden;
  border: 1px solid #d9e4dd;
  border-radius: 12px;
  background-color: #ffffff;
}

.image {
  width: 100%;
  height: 200px;
  object-fit: cover;
}

.body {
  display: flex;
  flex-direction: column;
  gap: 12px;
  padding: 16px;
}

.title {
  margin: 0;
  font-size: 20px;
}

.description {
  margin: 0;
  color: #4d5a53;
  line-height: 1.4;
}

.meta {
  display: flex;
  align-items: center;
  gap: 12px;
}

.price {
  margin: 0;
  font-size: 18px;
  font-weight: 700;
  color: #1e6bb8;
}

.rating {
  display: inline-flex;
  align-items: center;
  gap: 4px;
  color: #4d5a53;
}

.star {
  width: 16px;
  height: 16px;
}

.button {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 8px;
  width: 100%;
  padding: 10px 20px;
  border: 2px solid transparent;
  border-radius: 14px;
  background-color: #0ea5e9;
  color: #ffffff;
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
}

.button:hover {
  background-color: #0284c7;
}

.icon {
  width: 18px;
  height: 18px;
  filter: brightness(0) invert(1);
}
</style>

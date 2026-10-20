<script>
import ProductCard from './ProductCard.vue'

export default {
  name: 'ProductList',
  components: { ProductCard },
  props: {
    products: {
      type: Array,
      required: true,
    },
  },
  emits: ['add-to-cart'],
  methods: {
    onAddToCart(item) {
      this.$emit('add-to-cart', item)
    },
  },
}
</script>

<template>
  <main class="catalog">
    <ProductCard
      v-for="product in products"
      :key="product.id"
      :product="product"
      @add-to-cart="onAddToCart"
    />
  </main>
</template>

<style scoped>
.catalog {
  display: flex;
  flex-wrap: wrap;
  gap: 24px;
}
</style>

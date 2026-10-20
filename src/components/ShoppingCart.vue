<script>
export default {
  name: 'ShoppingCart',
  props: {
    items: {
      type: Array,
      required: true,
    },
  },
  computed: {
    total() {
      return this.items.reduce((sum, item) => sum + item.price * item.quantity, 0)
    },
    isEmpty() {
      return this.items.length === 0
    },
  },
}
</script>

<template>
  <section class="cart">
    <h2 class="cart__title">Корзина</h2>

    <p v-if="isEmpty" class="cart__empty">Корзина пуста. Добавьте товары из каталога.</p>

    <ul v-else class="cart__list">
      <li v-for="item in items" :key="item.id" class="cart__item">
        <div>
          <p class="cart__name">{{ item.title }}</p>
          <p class="cart__meta">{{ item.quantity }} × {{ item.price }} BYN</p>
        </div>
        <p class="cart__sum">{{ item.quantity * item.price }} BYN</p>
      </li>
    </ul>

    <p v-if="!isEmpty" class="cart__total">Итого: {{ total }} BYN</p>
  </section>
</template>

<style scoped>
.cart {
  margin-top: 32px;
  padding: 20px;
  border: 1px solid #d9e4dd;
  border-radius: 12px;
  background: #ffffff;
}

.cart__title {
  margin: 0 0 16px;
  font-size: 22px;
}

.cart__empty {
  margin: 0;
  color: #4d5a53;
}

.cart__list {
  margin: 0;
  padding: 0;
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 12px;
}

.cart__item {
  display: flex;
  justify-content: space-between;
  gap: 16px;
  padding-bottom: 12px;
  border-bottom: 1px solid #e8efe9;
}

.cart__name {
  margin: 0 0 4px;
  font-weight: 600;
}

.cart__meta {
  margin: 0;
  color: #4d5a53;
  font-size: 14px;
}

.cart__sum {
  margin: 0;
  font-weight: 700;
  color: #1e6bb8;
  white-space: nowrap;
}

.cart__total {
  margin: 16px 0 0;
  font-size: 18px;
  font-weight: 700;
}
</style>

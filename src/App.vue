<script>
import ProductList from './components/ProductList.vue'
import ShoppingCart from './components/ShoppingCart.vue'
import logo from './assets/house.png'
import bookImage from './assets/images.jpeg'
import searchIcon from './assets/search.svg'
import userIcon from './assets/user.svg'
import cartIcon from './assets/cart2.svg'

export default {
  name: 'App',
  components: { ProductList, ShoppingCart },
  data() {
    return {
      logo,
      searchIcon,
      userIcon,
      cartIcon,
      products: [
        {
          id: 1,
          title: 'Умный дом. Базовый курс',
          description: 'Электронная книга по сценариям освещения и климата.',
          image: bookImage,
          price: 29,
          rating: 4.2,
        },
        {
          id: 2,
          title: 'Digital House. Практикум',
          description: 'Цифровое пособие по настройке умного дома.',
          image: bookImage,
          price: 35,
          rating: 4.8,
        },
        {
          id: 3,
          title: 'Домашняя автоматизация',
          description: 'Сборник готовых схем и чек-листов для проекта.',
          image: bookImage,
          price: 19,
          rating: 4.0,
        },
      ],
      cartItems: [],
    }
  },
  methods: {
    addToCart(item) {
      const existing = this.cartItems.find((entry) => entry.id === item.id)
      if (existing) {
        existing.quantity += item.quantity
      } else {
        this.cartItems.push({ ...item })
      }
    },
  },
}
</script>

<template>
  <div class="page">
    <header class="header">
      <img class="logo" :src="logo" alt="Digital House" />
      <div>
        <h1>Digital House</h1>
        <p>Интернет-магазин цифровых товаров для дома</p>
      </div>
      <div class="header-actions">
        <button type="button" class="icon-button" aria-label="Поиск">
          <img :src="searchIcon" alt="" />
        </button>
        <button type="button" class="icon-button" aria-label="Профиль">
          <img :src="userIcon" alt="" />
        </button>
        <button type="button" class="icon-button" aria-label="Корзина">
          <img :src="cartIcon" alt="" />
          <span v-if="cartItems.length" class="badge">{{ cartItems.length }}</span>
        </button>
      </div>
    </header>

    <ProductList :products="products" @add-to-cart="addToCart" />
    <ShoppingCart :items="cartItems" />

    <footer class="footer">
      <p class="footer__brand">Digital House</p>
      <p class="footer__text">Цифровые товары для умного дома © 2026</p>
    </footer>
  </div>
</template>

<style scoped>
.page {
  max-width: 1100px;
  margin: 0 auto;
  padding: 32px 16px 64px;
}

.header {
  display: flex;
  align-items: center;
  gap: 16px;
  margin-bottom: 32px;
}

.logo {
  width: 72px;
  height: 72px;
  object-fit: contain;
}

.header h1 {
  margin: 0;
  font-size: 28px;
}

.header p {
  margin: 4px 0 0;
  color: #4d5a53;
}

.header-actions {
  display: flex;
  gap: 8px;
  margin-left: auto;
}

.icon-button {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  padding: 0;
  border: none;
  background: transparent;
  cursor: pointer;
}

.icon-button img {
  width: 22px;
  height: 22px;
}

.badge {
  position: absolute;
  top: 0;
  right: 0;
  min-width: 16px;
  height: 16px;
  padding: 0 4px;
  border-radius: 999px;
  background: #0ea5e9;
  color: #fff;
  font-size: 11px;
  line-height: 16px;
}

.footer {
  margin-top: 48px;
  padding-top: 20px;
  border-top: 1px solid #d9e4dd;
  text-align: center;
}

.footer__brand {
  margin: 0 0 4px;
  font-size: 15px;
  font-weight: 600;
  color: #1c2420;
}

.footer__text {
  margin: 0;
  font-size: 13px;
  color: #4d5a53;
}
</style>

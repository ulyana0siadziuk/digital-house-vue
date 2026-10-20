# Digital House (ЛР №4, Vue.js)

Интернет-магазин цифровых товаров на Vue.js. Вариант 3.

## Запуск

```bash
cd "C:\D\Study\7 sem\lab4-digital-house"
npm install
npm run dev
```

Открой адрес из терминала (обычно http://localhost:5173/).

## Что реализовано

- `ProductCard.vue` — карточка товара, кнопка «В корзину» генерирует событие `$emit('add-to-cart', …)`
- `ProductList.vue` — список карточек через `v-for`
- `ShoppingCart.vue` — отображение корзины (`v-if` / `v-for`)
- В `App.vue` массив `cartItems` пополняется по событию из карточки

## Структура

```
src/
  App.vue
  components/
    ProductCard.vue
    ProductList.vue
    ShoppingCart.vue
    QuantitySelector.vue
  assets/
```

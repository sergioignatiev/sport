<template>
  <div class="product-card">
    <img :src="product.image" :alt="product.title" class="product-image" />
    <div class="product-info">
      <h2 class="product-title">{{ product.title }}</h2>
      <p class="product-description">{{ product.description }}</p>
      <div class="product-footer">
        <span class="product-price">{{ product.price }} ₽</span>
        <button @click="addToCart" class="add-button">В корзину</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProductCard',
  data() {
    return {
      product: {
        title: 'Горный велосипед X-Trial 3000',
        description: 'Надёжный и лёгкий горный велосипед с амортизацией, дисковыми тормозами и 21 скоростью.',
        price: 28990,
        image: 'https://example.com/images/bike.jpg'
      }
    };
  },
  methods: {
    addToCart() {
      alert(`Товар \"${this.product.title}\" добавлен в корзину!`);
    }
  }
};
</script>

<style scoped>
.product-card {
  display: flex;
  flex-direction: column;
  border: 1px solid #ddd;
  border-radius: 10px;
  overflow: hidden;
  background-color: #fff;
  max-width: 100%;
  margin: 10px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.product-image {
  width: 100%;
  height: auto;
}

.product-info {
  padding: 10px;
  display: flex;
  flex-direction: column;
  line-height: 1.5;
}

.product-title {
  font-size: 18px;
  font-weight: bold;
  margin-bottom: 5px;
}

.product-description {
  font-size: 14px;
  color: #666;
  margin-bottom: 10px;
}

.product-footer {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.product-price {
  font-size: 16px;
  color: #FF6B00;
  font-weight: bold;
}

.add-button {
  background-color: #FF6B00;
  color: white;
  border: none;
  padding: 8px 12px;
  border-radius: 5px;
  font-size: 14px;
  cursor: pointer;
}

.add-button:hover {
  background-color: #e65a00;
}
</style>

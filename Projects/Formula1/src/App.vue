<template>
  <div>
    <div class="products-container">
      <h2>Products</h2>
      <div v-for="product in products" :key="product.id" class="product-item">
        <img :src="product.img" alt="product image">
        <div class="product-info">
          <div class="product-name">{{ product.name }}</div>
          <div class="product-price">{{ product.price }} €</div>
        </div>
        <button @click="addToCart(product)" class="add-to-cart-btn">Add to Cart</button>
      </div>
    </div>
    <div class="cart-container">
      <h2>Shopping Cart</h2>
      <ul>
        
        <li v-for="cartItem in cart" :key="cartItem.id" class="cart-item">
          
          <div class="cart-item-name">{{ cartItem.name }}</div>
          <div class="cart-item-price">{{ cartItem.price }} €</div>
          
        </li>
      </ul>
      <h3 class="total">Total: {{ total }}€</h3>
      <button @click="checkout()" class="checkout-btn">Checkout</button>
    </div>
    
  </div>
</template>
<script>
 import image from "./assets/Alpine.jpeg"
 import image2 from "./assets/Redbull.jpg"
 import image3 from "./assets/Astonmartin.jpg"
export default {
  data() {
    return {
      products: [
        { id: 1, name: 'Alpine', price: 900, img:image },
        { id: 2, name: 'Redbull', price: 700, img: image2 },
        { id: 3, name: 'Aston Martin', price: 800, img: image3 }
      ],
      cart: [],
    }
  },
  computed: {
    total() {
      return this.cart.reduce((acc, item) => acc + item.price, 0)
    }
  },
  methods: {
    addToCart(product) {
      this.cart.push(product)
    },
    checkout() {
      // Perform checkout here, for example by sending the cart data to an API
      this.cart = []
    }
  }
}
</script>
<style scoped>
.products-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  margin-bottom: 20px;
}

.product-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 400px;
  padding: 10px;
  margin-bottom: 10px;
  border: 1px solid gray;
}
  
  .product-name {
    font-weight: bold;
  }
  
  .product-price {
    font-style: italic;
  }
  
  .add-to-cart-btn {
    padding: 10px 20px;
    background-color: green;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  img {
    width: 200px;
    height: 100px;
    object-fit: cover;
  }
  .cart-container {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  
  .cart-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 400px;
    padding: 10px;
    margin-bottom: 10px;
    border: 1px solid gray;
  }
</style>
<template>
   <div class="cart">
      <h2>Корзина</h2>
      <button class="clear-cart" @click="$emit('clear-all-cart')">Очистить корзину</button>
      <span class="suma">Итого: {{sumPrice}} $</span>
      <hr>
      <div 
         class="product__cart"
         v-for="cart of productCart"
         :key="cart.id"
      >
         <h3 class="product__title">{{cart.title}}</h3>
         <img :src="require('../assets/'+ cart.img)" class="product__img">
         <p class="product__description">{{cart.description}}</p>
         <span class="product-price">Цена: {{cart.price}} $</span>
         <button @click="$emit('delete-cart', cart.id)" class="delete__cart">Убрать из корзины</button>
         <div class="counter__product">
            <button class="counter__product-minus" @click="$emit('minus', cart.id)">-</button>
            <div class="counter__product-input">{{cart.count}}</div>
            <button class="counter__product-plus" @click="$emit('plus', cart.id)">+</button>
         </div>
         
      </div>
   </div>
</template>

<script>
export default {
   name: 'product-cart',
   data(){
      return{
        
      }
   },
   props: ['productCart', 'sumPrice'],
   methods:{

   },
   mounted() {
      document.querySelector('.cart').style.top = window.pageYOffset + 65 + 'px'
      document.body.style.overflow = 'hidden'
   },
   beforeDestroy() {
      document.body.style.overflow = ''
   }
}
</script>

<style scoped lang="scss">
.cart{
   position: absolute;
   top: 70px;
   right: 10px;
   width: 1000px;
   height: calc(100vh - 70px);
   background-color: rgb(240, 240, 240);
   box-shadow: 0px 2px 17px 5px rgba(50, 50, 50, 0.54);
   overflow: auto;
   z-index: 101;
}
      
.suma{
   position: absolute;
   left: 50px;
   font-size: 30px;
   font-weight: 700;
}
h2{
   margin: 0 auto;
   font-size: 40px;
   font-family: cursive;
   font-weight: 700;
}

.product__cart {
   display: flex;
   position: relative;
   width: 950px;
   height: 200px;
   background: #fff;
   margin: 10px auto;
   .product__title {
      position: absolute;
      width: 100%;
      margin: 10px 0 ;
   }
   .product__img {
      max-width: 200px;
      height: 150px;
      margin: auto 0;
   }
   .product__description {
      height: 200px;
      width: 400px;
      overflow: auto;
      padding: 30px 10px;
   }
   .product-price{
      position: absolute;
      right: 0;
      top: 105px;
      width: 200px;
      height: 40px;
      font-size: 20px;
   }
}

   .delete__cart {
      margin: 10px 20px 0 auto;
      width: 190px;
      height: 40px;
      font-size: 17px;
      position: relative;
      background: #f3f0f1;
      border: none;
      border-radius: 32px;
      text-align: center;
      cursor: pointer;
      transition: all 0.1s ease-in-out;
      box-shadow: -6px -6px 10px rgba(255, 255, 255, 0.8),
      6px 6px 10px rgba(0, 0, 0, 0.2);
      color: #e40000;
      outline: none;
         &:hover {
            opacity: 0.8;
            box-shadow: -6px -6px 10px rgba(255, 255, 255, 0.76),
            6px 6px 10px rgba(0, 0, 0, 0.212);
         }
         &:active {
            opacity: 1;
            box-shadow: inset -4px -4px 8px rgba(255, 255, 255, 0.5),
            inset 8px 8px 16px rgba(0, 0, 0, 0.1);
            color: #8a0900;
         }
}

.counter__product {
   position: absolute;
   bottom: 0;
   right: 0;
   display: flex;
   justify-content: center;
   align-items: center;
   width: 195px;
   height: 69px;
   .counter__product-plus {
      width: 40px;
      height: 40px;
      cursor: pointer;
   }
   .counter__product-minus {
      @extend .counter__product-plus;
   }
   .counter__product-input {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 40px;
      width: 60px;
      font-size: 25px;
      border: 1px solid rgb(145, 145, 145);
      margin: 0 8px;
   }
}

.clear-cart {
   width: 200px;
   height: 50px;
   font-size: 18px;
   background: #f3f0f1;
   position: relative;
   background: #f3f0f1;
   margin: 15px;
   border: none;
   border-radius: 32px;
   text-align: center;
   cursor: pointer;
   transition: all 0.1s ease-in-out;
   box-shadow: -6px -6px 10px rgba(255, 255, 255, 0.8),
   6px 6px 10px rgba(0, 0, 0, 0.2);
   color: #e40000;
   outline: none;
   &:hover {
      opacity: 0.8;
      box-shadow: -6px -6px 10px rgba(255, 255, 255, 0.76),
      6px 6px 10px rgba(0, 0, 0, 0.212);
   }
   &:active {
      opacity: 1;
      box-shadow: inset -4px -4px 8px rgba(255, 255, 255, 0.5),
      inset 8px 8px 16px rgba(0, 0, 0, 0.1);
      color: #8a0900;
   }
   }



</style>
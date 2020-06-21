<template>
<div class="">
   <h2>Каталог</h2>
   <div class="bodyStor">

      <transition name="cartFull">
         <CardFullscreen
            v-if="cardFull" 
            v-bind:card="card"
            @close="Close"
            @add-to-cart='AddCard'
         />
      </transition>

      <Card 
         @card-product="cardProduct"
      />

      <transition name="cartProduct">
         <CartProduct 
            v-if="cartOpen" 
            :product-cart='productCart'
            :sum-price="sumPrice"
            @clear-all-cart="ClearAllCart"
            @delete-cart="DeleteCard"
            @plus="Plus"
            @minus='Minus'
         />
      </transition>
   </div>
</div>
</template>

<script>
import Card from "../components/Card"
import CardFullscreen from "../components/CardFullScreen";
import CartProduct from '../components/CartProduct'

export default {
   name: 'store',
   data: ()=>({
      card: [],
      cardFull: false,
      productCart: [],
      sumPrice: 0,
   }),
   props: ['cartOpen'],
   methods:{
      cardProduct(product){
         this.card = product
         this.cardFull = true
      },
      Close(){
         this.cardFull = false
      },
      AddCard(){
        if(!this.productCart.includes(this.card)){
           this.card.add = true
            this.productCart.push(this.card) 
            this.$emit('cart-product', this.productCart)
        }  
           this.sumPrice = 0,
               this.productCart.forEach(price => {
                  this.sumPrice =   this.sumPrice + price.price 
               });
                             
      },
      ClearAllCart(){
         this.productCart.forEach(e => e.add = false)
         this.productCart = []
         this.$emit('cart-product', this.productCart)
         this.sumPrice = 0,
               this.productCart.forEach(price => {
                    this.sumPrice =   this.sumPrice + price.price 
               });
      },
      DeleteCard(id){
         this.productCart.forEach(element => {
            if (element.id === id) {
               element.add = false
            }
         this.productCart = this.productCart.filter(elem => elem.id != id)
         });
         this.$emit('cart-product', this.productCart)
         this.sumPrice = 0,
               this.productCart.forEach(price => {
                    this.sumPrice =   this.sumPrice + price.price 
               });
      },
      Plus(id){
         this.productCart.forEach(e => {
            if(e.id === id){
               e.count = e.count + 1
               e.price = e.price + e.priceStatic
               this.sumPrice = 0,
               this.productCart.forEach(price => {
                  this.sumPrice =   this.sumPrice + price.price 
               });
            }
         })
      },
      Minus(id){
         this.productCart.forEach(e => {
            if((e.id === id) && (e.count != 0)){
               e.count = e.count - 1
               e.price = e.price - e.priceStatic
               this.sumPrice = 0,
               this.productCart.forEach(price => {
                  this.sumPrice =   this.sumPrice + price.price 
               });
            }
         })
      }
        
   },
   
   components:{
      Card, CardFullscreen, CartProduct, 
   }
}
</script>

<style scoped>
.bodyStor{
   display: flex;
   width: 100%;
   height: auto;

}
h2{
   margin: 0 auto;
   font-size: 40px;
   font-family: cursive;
   font-weight: 700;
}

.cartProduct-enter{
   opacity: 0;
}
.cartProduct-enter-active, .cartProduct-leave-active{
   transition: transform .2s linear;
}
.cartProduct-leave-to{
   opacity: 0;
}

.cartFull-enter{
   opacity: 0;
}
.cartFull-enter-active, 
.cartFull-leave-active{
   transition: opacity .2s linear;
   
}
.cartFull-leave-to{
   opacity: 0;
}


</style>
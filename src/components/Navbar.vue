<template>
   <nav class="nav">
      <div class="nav__logo">Test Stor</div>
      <div class="nav__link">
         <button 
            @click="$emit('cart-open')"  
            class="nav__link-btn" 
            :class="{'nav__link-btn--active': CartOpen}"
         >
         <div class="counter" v-if="countProduct > 0">{{countProduct}}</div>
         <p v-if="!CartOpen">Корзина</p>
         <p v-else>Закрыть</p>
         </button>
      </div>
   </nav>
</template>

<script>
export default {
   name: 'navigations',
   data(){
      return{

      }
   },
   props: ['CartOpen', 'countProduct'],
}
</script>

<style scoped lang='scss'>
.nav {
   position: fixed;
   display: flex;
   width: 100%;
   height: 60px;
   background-color: rgb(75, 74, 74);
   z-index: 1000;
   .nav__logo {
      display: flex;
      align-items: center;
      justify-content: flex-start;
      width: 30%;
      height: 100%;
      padding-left: 20px;
      background-color: rgba(255, 235, 205, 0.089);
      font-size: 40px;
      font-weight: 700;
      color: azure;
   }
}

.nav__link {
   display: flex;
   justify-content: flex-end;
   align-items: center;
   width: 70%;
   height: 100%;

   .nav__link-btn {
      height: 100%;
      width: 150px;
      border: none;
      outline: none;
      background: rgb(75, 74, 74);
      color: rgb(75, 74, 74);;
      font-size: 22px;
      font-family: Arial, Helvetica, sans-serif;
      font-weight: 700;
      transition: color background-color 0.2s linear;
      cursor: pointer;
      &:active{
         color: rgb(75, 74, 74);
      } 
      
   }
   .nav__link-btn--active{
      @extend .nav__link-btn;
      color: rgb(221, 0, 0)
   }
   .counter{
      display: flex;
      justify-content: center;
      align-items: center;
      position: absolute;
      top: 2px;
      right: 11px;
      width: 35px;
      height: 35px;
      color: #000;
      background-color: rgba(255, 255, 255, 0.938);
      border: 4px rgb(75, 74, 74) solid;
      border-radius: 50%;
      font-size: 22px;
      font-family: 'Franklin Gothic Medium', sans-serif;
      z-index: 0;
      }
      p{
         display: flex;
         align-items: center;
         justify-content: center;
         width: 120px;
         height: 30px;
         background-color: azure;
         border-radius: 5px;
      }
} 


</style>
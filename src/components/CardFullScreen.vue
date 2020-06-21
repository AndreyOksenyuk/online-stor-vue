<template>
   <div class="card__fullscreen">
      <button class="card__fullscreen-close" @click="$emit('close')">X</button>
      <div class="card-fullscreen-inner">
         
         <div class="card__fullscreen-img">
            <h3 class="card__fullscreen-title">{{card.title}}</h3>
            <img :src="require('../assets/'+ card.img)"  alt="card" class="img">
         </div> 
         <p class="card__fullscreen-description">{{card.description}}</p>
         <span class="card__fullscreen-price">Цена: {{card.priceStatic}} $</span>
      </div>
      <button class="addToCart-btn" @click="$emit('add-to-cart')">Добавить в корзину</button>
      <p v-if="card.add" class="already-added">Товар добавлен в корзину</p>
   </div>
</template>

<script>
export default {
   data(){
      return{

      }
   },
   props: ['card'],
   mounted() {
      document.querySelector('.card__fullscreen').style.top = window.pageYOffset + 65 + 'px'
      document.body.style.overflow = 'hidden'
   },
   beforeDestroy() {
      document.body.style.overflow = ''
   }
}
</script>

<style scoped lang='scss'>
.card__fullscreen {
   position: absolute;
   top: 70px;
   left:50%;
   transform: translate(-50%, );
   width: 90%;
   height: 90%;
   z-index: 100;
   background: rgb(241, 241, 241);
   border: 1px #000 solid;
   border-radius: 10px;

   .card__fullscreen-close{
      position: absolute;
      top: 10px;
      right: 20px;
      width: 60px;
      height: 60px;
      font-size: 25px;
      outline: none;
      color: rgb(92, 92, 92);
      border: 1px rgb(114, 114, 114) solid;
      border-radius: 50%;
      background-color: rgba(136, 136, 136, 0.192);
      cursor: pointer;
      z-index: 100;
         &:hover{
            background-color: rgba(136, 136, 136, 0.534);
         }
         &:active{
            transform: scale(0.95)
         }
   }
   .card-fullscreen-inner {
      display: flex;
      justify-content: center;
      align-items: center;
      flex-wrap: wrap;
      position: relative;
      width: 100%;
      height: 90%;
      .card__fullscreen-img {
         display: flex;
         justify-content: center;
         align-items: center;
         width: 700px;
         height: 700px;
         margin-top: 10px;
         box-shadow: -5px 10px 20px rgba(114, 114, 114, 0.199);
         background-color: #fff;
         .img{
            width: 600px;
            cursor: pointer;
         }

      }
      .card__fullscreen-title {
         position: absolute;
         top: 20px;
         width: 400px;
         font-size: 30px;
      }
      .card__fullscreen-description {
         width: 300px;
         margin-left: 50px;
      }
      .card__fullscreen-price{
         display: flex;
         align-items: center;
         justify-content: center;
         width: 400px;
         height: 70px;
         font-size: 30px;
      }
   }
}

.already-added{
   color: green;
   margin-top: 10px;
}
.addToCart-btn{
   font-size: 16px;
   font-weight: 700;
   color: white;
   text-decoration: none;
   padding: .8em 1em calc(.8em + 3px);
   border-radius: 3px;
   background: rgb(64,199,129);
   box-shadow: 0 -3px rgb(53,167,110) inset;
   transition: 0.2s;
   outline: none;
   cursor: pointer;
   &:hover{
      background: rgb(53, 167, 110);
   }
   &:active{
      background: rgb(33,147,90);
      box-shadow: 0 3px rgb(33,147,90) inset
   }
}


</style>
<template>
  <div class="card">
    <Selector 
      class="selector"
      :cards='cards'
      @select-product="SelectProduct"
    />
  <div 
    class="product__card"
    :class="{'product__card-add': product.add}" 
    v-for="product in selectProduct" :key="product.id"
    @click="Card(product)"
  >
    <p v-if="product.add" class="already-added">Товар уже в корзине</p>
    <img :src="require('../assets/'+ product.img)"  alt="card" class="product__card-img">
    <h3 class="product__card-title">{{product.title}}</h3>
    <p class="product__card-description">{{product.description}}</p>
  </div>

  </div>
</template>

<script>
import Selector from './Selector'

export default {
  data(){
    return{
      selectProduct: [],
      cards:[
        {
          id: 1,
          add: false,
          count: 1,
          tipe: 'Смартфоны',
          priceStatic: 1000,
          price: 1000,
          img: 'iphon7.jpg', 
          title: 'iPhon 7', 
          description: 'Екран (4.7", IPS, 1334x750)/ Apple A10 Fusion/ основна камера: 12 Мп, фронтальна камера: 7 Мп/ RAM 2 ГБ/ 32 ГБ вбудованої памяті/ 3G/ LTE/ GPS/ Nano-SIM/ iOS 10'
        },
        {
          id: 2,
          add: false,
          count: 1,
          tipe: 'Смартфоны',
          priceStatic: 1500,
          price: 1500,
          img: 'meizuM6.jpg', 
          title: 'iPhon 8', 
          description: 'Екран (6.1", IPS (Liquid Retina HD), 1792x828) / Apple A13 Bionic / основна подвійна камера: 12 Мп + 12 Мп'
        },
        {
          id: 3, 
          add: false,
          count: 1,
          tipe: 'Смартфоны',
          priceStatic: 2230,
          price: 2230,
          img: 'samsungA6.jpg',
          title: 'iPhon X', 
          description: 'Екран (6.1", IPS (Liquid Retina HD), 1792x828) / Apple A13 Bionic / основна подвійна камера: 12 Мп + 12 Мп'
        },
        {
          id: 4,
          add: false,
          count: 1,
          tipe: 'Смартфоны',
          priceStatic: 1600,
          price: 1600,
          img: 'iphon7.jpg', 
          title: 'iPhon 7', 
          description: 'Екран (6.1", IPS (Liquid Retina HD), 1792x828) / Apple A13 Bionic / основна подвійна камера: 12 Мп + 12 Мп'
        },
        {
          id: 5,
          add: false,
          count: 1,
          tipe: 'Смартфоны',
          priceStatic: 2000,
          price: 2000,
          img: 'iphon7.jpg', 
          title: 'iPhon 7', 
          description: 'Екран (6.1", IPS (Liquid Retina HD), 1792x828) / Apple A13 Bionic / основна подвійна камера: 12 Мп + 12 Мп'
        },
        {
          id: 6,
          add: false,
          count: 1,
          tipe: 'Смартфоны',
          priceStatic: 1550,
          price: 1550,
          img: 'meizuM6.jpg', 
          title: 'iPhon 8', 
          description: 'Екран (6.1", IPS (Liquid Retina HD), 1792x828) / Apple A13 Bionic / основна подвійна камера: 12 Мп + 12 Мп'
        },
        {
          id: 7, 
          add: false,
          count: 1,
          tipe: 'Смартфоны',
          priceStatic: 1000,
          price: 1000,
          img: 'samsungA6.jpg',
          title: 'iPhon X', 
          description: 'Екран (6.1", IPS (Liquid Retina HD), 1792x828) / Apple A13 Bionic / основна подвійна камера: 12 Мп + 12 Мп'
        },
        {
          id: 8,
          add: false,
          count: 1,
          tipe: 'Смартфоны',
          priceStatic: 1000,
          price: 1000, 
          img: 'meizuM6.jpg',
          title: 'Meizu m6 note', 
          description: 'Екран (6.1", IPS (Liquid Retina HD), 1792x828) / Apple A13 Bionic / основна подвійна камера: 12 Мп + 12 Мп'
        },
        {
          id: 9,
          add: false,
          count: 1,
          tipe: 'Смартфоны',
          priceStatic: 1000,
          price: 1000,
          img: 'iphon7.jpg', 
          title: 'iPhon 7', 
          description: 'Екран (6.1", IPS (Liquid Retina HD), 1792x828) / Apple A13 Bionic / основна подвійна камера: 12 Мп + 12 Мп'
        },
        {
          id: 10,
          add: false,
          count: 1,
          tipe: 'Смартфоны',
          priceStatic: 1000,
          price: 1000,
          img: 'meizuM6.jpg', 
          title: 'iPhon 8', 
          description: 'Екран (6.1", IPS (Liquid Retina HD), 1792x828) / Apple A13 Bionic / основна подвійна камера: 12 Мп + 12 Мп'
        },
        {
          id: 11,
          add: false,
          count: 1,
          tipe: 'Планшеты',
          priceStatic: 4300,
          price: 4300,
          img: 'planshet-lenovo.jpg', 
          title: 'Lenovo Tab P10', 
          description: 'Екран 10.1" IPS (1920x1200) ємнісний MultiTouch / Qualcomm Snapdragon 450 (1.8 ГГц) / RAM 4 ГБ / 64 ГБ вбудованої памяті + microSD / Wi-Fi / Bluetooth 4.2 / основна камера 8 Мп, фронтальна - 5 Мп / A-GPS / ГЛОНАСС / Android 8.0 (Oreo) / 440 г / чорний'
        },
        {
          id: 12,
          add: false,
          count: 1,
          tipe: 'Планшеты',
          priceStatic: 4300,
          price: 4300,
          img: 'planshet-lenovo.jpg', 
          title: 'Lenovo Tab P10', 
          description: 'Екран 10.1" IPS (1920x1200) ємнісний MultiTouch / Qualcomm Snapdragon 450 (1.8 ГГц) / RAM 4 ГБ / 64 ГБ вбудованої памяті + microSD / Wi-Fi / Bluetooth 4.2 / основна камера 8 Мп, фронтальна - 5 Мп / A-GPS / ГЛОНАСС / Android 8.0 (Oreo) / 440 г / чорний'
        },
        {
          id: 13,
          add: false,
          count: 1,
          tipe: 'Планшеты',
          priceStatic: 4000,
          price: 4000,
          img: 'planshet-lenovo.jpg', 
          title: 'Lenovo Tab P12', 
          description: 'Екран 10.1" IPS (1920x1200) ємнісний MultiTouch / Qualcomm Snapdragon 450 (1.8 ГГц) / RAM 4 ГБ / 64 ГБ вбудованої памяті + microSD / Wi-Fi / Bluetooth 4.2 / основна камера 8 Мп, фронтальна - 5 Мп / A-GPS / ГЛОНАСС / Android 8.0 (Oreo) / 440 г / чорний'
        },
        {
          id: 14,
          add: false,
          count: 1,
          tipe: 'Ноутбуки',
          priceStatic: 6000,
          price: 6000,
          img: 'mac-book-pro.jpg', 
          title: 'Apple MacBook Pro', 
          description: 'Экран 13.3" IPS (2560x1600), глянцевый / Intel Core i5-8257U (1.4 - 3.9 ГГц) / RAM 8 ГБ / SSD 512 ГБ / Intel Iris Plus Graphics 645 / Wi-Fi / Bluetooth / macOS Catalina / 1.4 кг / серый'
        },
        {
          id: 15,
          add: false,
          count: 1,
          tipe: 'Ноутбуки',
          priceStatic: 7000,
          price: 7000,
          img: 'mac-book-pro.jpg', 
          title: 'Apple MacBook Pro', 
          description: 'Экран 13.3" IPS (2560x1600), глянцевый / Intel Core i5-8257U (1.4 - 3.9 ГГц) / RAM 8 ГБ / SSD 512 ГБ / Intel Iris Plus Graphics 645 / Wi-Fi / Bluetooth / macOS Catalina / 1.4 кг / серый'
        },
        {
          id: 14,
          add: false,
          count: 1,
          tipe: 'Ноутбуки',
          priceStatic: 6000,
          price: 6000,
          img: 'hp.jpg', 
          title: 'HP Omen', 
          description: 'Экран 15.6" IPS (1920x1080) Full HD, матовый / Intel Core i5-9300H (2.4 - 4.1 ГГц) / RAM 8 ГБ / SSD 256 ГБ / nVidia GeForce GTX 1650, 4 ГБ / без ОД / LAN / Wi-Fi / Bluetooth / веб-камера / DOS / 2.32 кг / черный'
        },
        {
          id: 15,
          add: false,
          count: 1,
          tipe: 'Ноутбуки',
          priceStatic: 7000,
          price: 7000,
          img: 'mac-book-pro.jpg', 
          title: 'Apple MacBook Pro', 
          description: 'Экран 13.3" IPS (2560x1600), глянцевый / Intel Core i5-8257U (1.4 - 3.9 ГГц) / RAM 8 ГБ / SSD 512 ГБ / Intel Iris Plus Graphics 645 / Wi-Fi / Bluetooth / macOS Catalina / 1.4 кг / серый'
        },
        {
          id: 16,
          add: false,
          count: 1,
          tipe: 'Ноутбуки',
          priceStatic: 6000,
          price: 6000,
          img: 'mac-book-pro.jpg', 
          title: 'Apple MacBook Pro', 
          description: 'Экран 13.3" IPS (2560x1600), глянцевый / Intel Core i5-8257U (1.4 - 3.9 ГГц) / RAM 8 ГБ / SSD 512 ГБ / Intel Iris Plus Graphics 645 / Wi-Fi / Bluetooth / macOS Catalina / 1.4 кг / серый'
        },
        {
          id: 17,
          add: false,
          count: 1,
          tipe: 'Ноутбуки',
          priceStatic: 6000,
          price: 6000,
          img: 'hp.jpg', 
          title: 'HP Omen', 
          description: 'Экран 15.6" IPS (1920x1080) Full HD, матовый / Intel Core i5-9300H (2.4 - 4.1 ГГц) / RAM 8 ГБ / SSD 256 ГБ / nVidia GeForce GTX 1650, 4 ГБ / без ОД / LAN / Wi-Fi / Bluetooth / веб-камера / DOS / 2.32 кг / черный'
        },
        {
          id: 18,
          add: false,
          count: 1,
          tipe: 'Ноутбуки',
          priceStatic: 6000,
          price: 6000,
          img: 'mac-book-pro.jpg', 
          title: 'Apple MacBook Pro', 
          description: 'Экран 13.3" IPS (2560x1600), глянцевый / Intel Core i5-8257U (1.4 - 3.9 ГГц) / RAM 8 ГБ / SSD 512 ГБ / Intel Iris Plus Graphics 645 / Wi-Fi / Bluetooth / macOS Catalina / 1.4 кг / серый'
        },
        {
          id: 19,
          add: false,
          count: 1,
          tipe: 'Ноутбуки',
          priceStatic: 6000,
          price: 6000,
          img: 'hp.jpg', 
          title: 'HP Omen', 
          description: 'Экран 15.6" IPS (1920x1080) Full HD, матовый / Intel Core i5-9300H (2.4 - 4.1 ГГц) / RAM 8 ГБ / SSD 256 ГБ / nVidia GeForce GTX 1650, 4 ГБ / без ОД / LAN / Wi-Fi / Bluetooth / веб-камера / DOS / 2.32 кг / черный'
        },
       
       
      ]
    }
  },
  methods:{
    Card(product){
      this.$emit('card-product', product)
    },
    SelectProduct(arr) {
      this.selectProduct = arr
    }
   
  },
  mounted(){
    this.selectProduct = this.cards
  },
   components: {
      Selector
    }

}
</script>


<style scoped lang="scss">
.selector{
  position: absolute;
  top: 80px;
}
.card {
  display: flex;
  flex-wrap: wrap;
  width: 1200px;
  margin: 0 auto; 
  background-color: rgba(235, 235, 235, 0.418);
  padding: 30px; 
  border-radius: 5px;
}

.product__card {
  position: relative;
  width: 23%;
  height: 400px;
  margin: 10px;
  padding: 8px;
  transition: transform .2s linear;
  cursor: pointer;
  border-radius: 10px;
  background: rgb(253, 253, 253) radial-gradient(circle at 50% 0, rgba(255,255,255,.65), rgba(255,255,255,.35));
  box-shadow:
  inset rgba(0,0,0,.6) 0 -3px 8px,
  inset rgba(252,255,255,.7) 0 3px 8px,
  rgba(0,0,0,.8) 0 3px 8px -3px;
  &:hover{
      transform: scale(1.09);
  }
    .already-added  {
      position: absolute;
      bottom: 10px;
      left: 45px;
      color: rgb(0, 148, 0);
      font-size: 18px;
      font-weight: 700;
    }
    .product__card-img {
      width: 200px;
      margin-bottom: 10px;
    }
    .product__card-title {
      margin-bottom: 10px;
    }

}
.product__card-add{
  @extend .product__card;
  background-color: rgba(176, 253, 176, 0.205);
}

</style>
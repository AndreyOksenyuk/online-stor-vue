<template>
   <div>
      <select name="select" id="select" @change="SelectChange">
         <option 
            v-for="card in productType"
            :key="card"
            :value="card"
            
         >{{card}}
         </option>
         
      </select>    
   </div>
</template>

<script>
export default {
   name: 'selector',
   props: ['cards'],
   data() {
      return {
         productType: ['Все', 'Планшеты', 'Смартфоны', 'Ноутбуки'],
         SelectProduct: [],
      }
   },
   methods: {
      SelectChange() {
         this.SelectProduct = []
         let tipe = document.querySelector('#select').value
         this.cards.forEach(e => {
            if(e.tipe === tipe || tipe === 'Все'){
               this.SelectProduct.push(e)
            }
         });
         this.$emit('select-product', this.SelectProduct)
      }
   }

}
</script>

<style scoped lang="scss">
#select{
   position: absolute;
   top: -10px;
   right: 0;
   width: 150px;
   padding: 3px 5px;
   font-size: 15px;
   border: 1px solid rgb(153, 153, 153);
   border-radius: 10px;
   color: rgb(53, 53, 53);
   outline: none;
   background-color: rgb(238, 238, 238);
   option{
   border-radius: 10px;
   font-size: 15px;
   border: 2px solid rgb(153, 153, 153);
   color: rgb(53, 53, 53);
   }
}

</style>
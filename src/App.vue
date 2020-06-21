<template>
  <div id="app">
    <Nav 
      @cart-open="CartOpen" 
      :cart-open="cartOpen"
      :count-product="countProduct"
    />
    <Stor 
      :cart-open="cartOpen"
      @cart-product="CountCart"
      />
  </div>
  
</template>

<script>
import Nav from './components/Navbar'
import Stor from './views/Store'
export default {
  name: 'app',
  data(){
    return{
      cart: [],
      cartBasket: [],
      cartOpen: false,
      countProduct: 0,
    }
  },
  methods:{
    CartOpen(){
      this.cartOpen = !this.cartOpen
    },
    CountCart(num){
      this.countProduct = num.length 
    }
  },
 
  components:{
    Nav, Stor
  },

}
</script>


<style lang="scss">
*{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

</style>

// @import 'node_modules/bootstrap/scss/bootstrap';
// @import 'node_modules/bootstrap-vue/src/index.scss';

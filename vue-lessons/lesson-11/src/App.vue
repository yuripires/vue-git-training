<template>
<div>
  <product-component  @add-to-cart="updateCart"></product-component>
  <div style="text-align: center"> Cart({{ cart }})</div>
</div>
</template>

<script>
import productComponent from './components/productComponent.vue'

export default {
  components:{
    productComponent,
  },
  
  name: 'App',
  data() {
    return {
      cart:0,
    }
  },
  methods:{
    updateCart(valor) {
      this.cart += valor;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.infoImage {
  width: 80px;
  height: 120px;
}
#navigator {
  margin-top: -40px;
  margin-left: -20px;
  margin-right: -20px;
  padding: 70px;
  background-image: linear-gradient(120deg, #8fd3f4 0%, #84fab0 100%);
}
.color-box{
  width: 40px;
  height: 40px;
  margin-top: 5px;
}
.disabledButton{
  background-color: rgb(255, 255, 255);
}

</style>

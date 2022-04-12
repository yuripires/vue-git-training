<template>
  <product-component></product-component>
  
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
      product: 'Socks',
      brand: 'Vue Mastery',
      selectedVariant: 0,
      
      link: 'https://shopee.com.br/Meia-Cano-Longo-Naruto-Akatsuki-Anim%C3%AA-i.349214594.5278560019',
      details:["80% cotton","20% polyester","Gender-Neutral"],
      variants: [{
        variantId: 2234,
        variantModel: "Classic",
        variantImage: 'https://a-static.mlcdn.com.br/618x463/kit-3-meias-cano-alto-estampadas-naruto-fbs/lojadivertidas/f23467fa909e11ebac5b4201ac1850e0/365a99db430732b7ad8bf659d30f503c.jpg',
        variantQuantity: 10,
        onSale: true,
      },
      {
        variantId: 2235,
        variantModel: "Long",
        variantImage: 'https://http2.mlstatic.com/D_NQ_NP_984276-MLB48051489737_102021-O.jpg',
        variantQuantity: 0,
        onSale: false,
      }],

      cart:0,
    }
  },

  methods:{
    addCart(){
      this.cart  ++;
    },

    updateProduct(index){
      this.selectedVariant = index
  },
  subCart(){
    this.cart --;
  }
  },
  computed:{
    title(){ if (this.variants[this.selectedVariant].onSale == true ){return 'On Sale'+ ' ' + this.brand + ' ' + this.product}
      else{ return this.brand + ' ' + this.product}
    },
    image(){
      return this.variants[this.selectedVariant].variantImage
    },
    inStock(){
      return this.variants[this.selectedVariant].variantQuantity
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

<template>
    <body>
    <div id="navigator"></div>
    <div id="app">
      <h1>{{ title }}</h1>

      <div class="infoImage">
        <img :src="image" />
      </div>
      
      <p v-if="inStock"> In Stock</p> 
      <p v-else> Out of Stock</p>
      <a :href="link" target="blank"> link for the shop </a>
      
      
      <li v-for="detail in details" :key="detail">
        <p>{{ detail }}</p>
      </li>

      <div v-for="(variant,index) in variants" 
      :key="variant.variantId"
      class="color-box">
        <p @mouseover="updateProduct(index)">
          {{ variant.variantModel }}
        </p>
      </div>

      <button @click="addCart" :disabled="!inStock" :class="{disabledButton: !inStock}">Add to cart</button>
      <button @click="subCart" :disabled="!inStock" :class="{disabledButton: !inStock}">Remove from the cart</button>
      

      <div>{{ cart }}</div>
    </div>
  </body>
</template>

<script>
export default {
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
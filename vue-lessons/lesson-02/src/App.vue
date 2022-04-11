<template>
  <div id="app">
    <h1>{{ product }}</h1>
    <img :src="image">
    <a :href="link" target="blank">link for the shop </a>
    
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      product: 'Socks',
      image: 'https://a-static.mlcdn.com.br/618x463/kit-3-meias-cano-alto-estampadas-naruto-fbs/lojadivertidas/f23467fa909e11ebac5b4201ac1850e0/365a99db430732b7ad8bf659d30f503c.jpg',
      link: 'https://shopee.com.br/Meia-Cano-Longo-Naruto-Akatsuki-Anim%C3%AA-i.349214594.5278560019',
    }
  },
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
</style>

<template>
  <CommonHeader/>
  <header>
    <div id=title>
     <h1>Bitcoin today</h1>
  </div>
</header>
    <body>
      <p>{{ current_price }}</p>
       <!--img id=bitcoin src="../public/Bitcoin.png"/-->
</body>
  <footer>
    <div id=footer>
       <h1>Bitcoin prices</h1>
  </div>
</footer>
</template>

<script>
//import axios from 'axios'

import CommonHeader from './components/common/header.vue';

export default {
  name: 'App',
  components: {
    CommonHeader
  },
  data: () => ({
    current_price: 10,
    
  }),
  mounted() {
    
    //axios.get('https://api.coingecko.com/api/v3/coins/bitcoin').then((response) => {
    //  this.current_price = response.data.market_data.current_price.brl
    //});
    
  }
}

</script>

<style>

@import url('https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,300;0,400;0,500;0,700;1,300;1,400;1,500;1,700&display=swap');

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Roboto', sans-serif;
  font-size: 15px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
  width: 100%;
}
</style> 
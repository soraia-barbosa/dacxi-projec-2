<template>
  
  <header>
    <div id=title>
   <h1>Bitcoin today</h1>
  </div>
</header>

  <p>{{ current_price }}</p>
  
  <ul>
    <li v-for="item in items" v-bind:key="item.id">
      <p>Id: {{ item.id }}</p>
      <p>Symbol: {{ item.symbol }}</p>
    </li>
  </ul>
</template>

<script>
import axios from 'axios'
export default {
  name: 'App',
  components: {
    
  },
  data: () => ({
    current_price: 0,
    items: [
      {
        id: "exemp",
        symbol: "exemplo"
      }
    ]
  }),
  mounted() {
    
    axios.get('https://api.coingecko.com/api/v3/coins/bitcoin').then((response) => {
      this.current_price = response.data.market_data.current_price.brl
    });
    axios.get('https://api.coingecko.com/api/v3/coins/list').then((response) => {
      this.items = response.data;
      this.$forceUpdate();
    });
  }
}
</script>

<style>

*{

  margin: 0;
  padding: 0;
}

header{

  background-color: black;
  width: 100%;
  height: 60px;
  
  
}

#title {

  color: white;
  padding: 10px;

 }
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0px;
}
</style> 
<template>
  
  <header>
    <div id=title>
     <h1>Bitcoin today</h1>
  </div>
</header>
    <body>
      <p>{{ current_price }}</p>
       <img id=bitcoin src="../public/Bitcoin.png"/>
</body>
  <footer>
    <div id=footer>
       <h1>Bitcoin prices</h1>
  </div>
</footer>
</template>

<script>
import axios from 'axios'
export default {
  name: 'App',
  components: {
    
  },
  data: () => ({
    current_price: 0,
    
  }),
  mounted() {
    
    axios.get('https://api.coingecko.com/api/v3/coins/bitcoin').then((response) => {
      this.current_price = response.data.market_data.current_price.brl
    });
    
  }
}

</script>

<style>
*{
  margin: 0 0;
  padding: 0;
}
header{
  background-color: black;
  width: 100%;
  height: 60px;
  margin-right: 0;
}
#title, #footer {
  color: white;
  padding: 10px;
 }

 body{
  height: 100%;
  
 }

 p {
   margin-top: 70px;
 }

 #bitcoin {
  width: 300px;
  margin-top: 50px;
  margin-bottom: 70px;
 }
footer{
  background-color: black;
  width: 100%;
  height: 60px;
  margin: auto;
  bottom: 0;
}

@media screen and (min-width: 300px){
    body {
      height: 100%;
      display: flex;
      flex-grow: 1;
    }
  
    header, footer {
      margin-right: 0;
      
    }
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
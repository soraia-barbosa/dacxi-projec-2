<template>
  <CommonHeader @chooseCoin="searchCoin" :coin-list="coinList"/>
  <Coin v-if="currentCoinData !== null" :coin="currentCoin" :coinData="currentCoinData"/> 
</template>

<script>

import axios from 'axios'

import CommonHeader from './components/common/header.vue';
import Coin from './components/coin.vue';

export default {
  name: 'App',
  components: {
    CommonHeader,
    Coin,
  },
  data: () => ({
    currentCoin: "bitcoin",
    currentCoinData: null,
    coinList: null,    
  }),
  mounted() {
    
    axios.get('https://api.coingecko.com/api/v3/coins/list').then((response) => {
      this.coinsList = response.data;
    });

    if(this.currentCoinData === null) {
      this.searchCoin();
    }    
    
  },

  methods: {
    
    searchCoin(event = null) {

      if(event){
        this.currentCoin = event.coinId;
      }
        
      axios.get('https://api.coingecko.com/api/v3/coins/' + this.currentCoin).then((response) => {
        this.currentCoinData = response.data;
      });

    }

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
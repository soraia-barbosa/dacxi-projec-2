<template>
    <div>
        <h1>Bitcoin today {{ Info }}</h1>
    </div>
    
  </template>
  
  <script>
  import axios from "axios";
  export default {
    name: 'FirstComponent',
    data() {
        return {
            Info:{},
        };
    },
    create() {
        this.getinfo();
    },
    methods: {
        getInfo(){
            axios
         .get('https://api.coingecko.com/api/v3/coins/list')
         .then((res) => {
           this.Info = res.data;
         })
         
     },
   },
  };
  
  </script>
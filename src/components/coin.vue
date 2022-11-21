<template>
    <div class="max-width">
        
        <div class="container">
            <div class="row">
                <div class="col-12">
                    <h1>{{ coinData.name }}</h1>
                    <div>
                        <h3>Coin description</h3>
                        <div v-html="coinData.description.en"></div>
                    </div>
                </div>
            </div>
            <div class="row">
                <div class="col-12">
                    <h4>Current price for follow currencies</h4>
                </div>
                <div class="col-4">
                    <p>BRL</p>
                    <p>{{ coinData.market_data.current_price.brl.toFixed(2) }}</p>
                </div>
                <div class="col-4">
                    <p>USD</p>
                    <p>{{ coinData.market_data.current_price.usd.toFixed(2) }}</p>
                </div>
                <div class="col-4">
                    <p>EUR</p>
                    <p>{{ coinData.market_data.current_price.eur.toFixed(2) }}</p>
                </div>
            </div>
            <div class="row">
                <div class="col-12">
                    <h4>See prices in another date</h4>
                </div>
                <div class="form-group">
                    <input @change="dateChanged" class="form-control" type="date" id="start" name="trip-start" min="2010-01-01" :max="today">
                </div>
            </div>
            <div v-if="coinHistory" class="row">
                <div class="col-12">
                    <h4>Price for date {{ lastDateFormated }}</h4>
                </div>
                <div class="col-4">
                    <p>BRL</p>
                    <p>{{ coinHistory.market_data.current_price.brl.toFixed(2) }}</p>
                </div>
                <div class="col-4">
                    <p>USD</p>
                    <p>{{ coinHistory.market_data.current_price.usd.toFixed(2) }}</p>
                </div>
                <div class="col-4">
                    <p>EUR</p>
                    <p>{{ coinHistory.market_data.current_price.eur.toFixed(2) }}</p>
                </div>
            </div>
        </div>
    </div>
</template>
<script>

import axios from 'axios'

export default {
    name: "Coin",
    props: {
        coin: {
            type: String,
            required: true,
        },
        coinData: {
            type: Object,
            required: true,
        }
    },
    data: () => ({
        coinHistory: null,
        lastDate: null,
    }),
    mounted() {
        console.log(this.coinData);
        console.log(this.today);
    },
    computed: {
        today() {
            let date = new Date();
            return date.getFullYear() + '-' + (date.getMonth() + 1) + '-' + date.getDate();
        },
        lastDateFormated() {
            return this.lastDate ? this.lastDate.split('-').join('/') : '';
        }
    },
    methods: {
        dateChanged(event) {

            let date = event.target.value;
            date = date.split('-');
            this.lastDate = date[2] + '-' + date[1] + '-' + date[0];
            
            axios.get('https://api.coingecko.com/api/v3/coins/' + this.coin + '/history?date=' + this.lastDate).then((response) => {
              this.coinHistory = response.data;
            });

            
        }
    }
}
</script>
<style scoped>

    .max-width {
        width: 100%;
        text-align: left;
    }
    
 .col-12{
        margin-top: 15px;
    }

</style>

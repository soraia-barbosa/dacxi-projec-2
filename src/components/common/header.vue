<template>
    <header>
        <div class="logo">
            <img src="../../assets/img/logo.png" alt="logo"/>
            <p>Dacxi Tech Challenge</p>            
        </div>
        <div class="search">
            <div class="input">
                <input @blur="clearResults" @keyup="searchStart" name="search" id="search">
                <label for="search">
                    <i class="fa-sharp fa-solid fa-magnifying-glass"></i>
                </label>                
            </div>            
            <div class="results">
                <ul v-if="results.length > 0">
                    <li v-for="coin in results" :key="coin.id">
                        <p @click="$emit('chooseCoin', {coinId: coin.id})">{{ coin.name }}</p>
                    </li>
                </ul>
            </div>
        </div>
    </header>
</template>
<script>
export default {
    name: "CommonHeader",
    props: {
        coinList: {
            type: Array,
            required: false,
            default: [],
        },        
    },
    data: () => ({
        results: [],
    }),
    methods: {
        clearResults() {
            this.results = [];
        },
        chooseCoin(coinId) {
            this.$emit('chooseCoin', {
                coinId
            });
        },
        searchStart(event) {

            let searchValue = event.target.value.toLowerCase();

            this.results = this.coinList.filter((coin) => {
                return coin.name.toLowerCase().search(searchValue) > -1 || coin.symbol.toLowerCase().search(searchValue) > -1;
            });

            if(this.results.length === 0) {
                this.results.push(
                    {
                        "id": "not found",
                        "symbol": "not found",
                        "name": "No coins found"
                    }
                );
            }
        }
    }
}
</script>
<style scoped>

    header {
        display: flex;
        flex-direction: row;
        background-color: #1e1e1e;
        color: #fff;
    }

    header > div {
        flex: 0 0 50%;
        width: 50%;
        padding: 15px;
    }

    header > div.logo img {
        width: 32px;
        height: 32px;
        display: inline-block;
    }

    header > div.logo {
        line-height: 32px;
        display: flex;
        align-content: left;
    }

    header > div.logo p {
        margin-left: 15px;
        font-weight: 700;
        display: inline-block;
        font-size: 14px;
        height: 25px;
        margin-bottom: 0;
    }
    
    header .search {
        position: relative;
        text-align: right;
    }

    header .search .input {
        position: relative;
        display: inline-block;
        text-align: left;
        overflow: hidden;        
    }

    header .search .input label {
        position: relative;
        transition: top 0.2s ease-in;
        width: 32px;
        height: 25px;
        z-index: 2;
        top: 0;
    }

    header .search .input input {
        transition: width 0.2s ease-in;
        width: 0px;
        height: 25px;
        border: 0;
        border-bottom: 1px solid #fff;
        padding: 4px 0;
        background-color: transparent;
        outline: none;
        color: #fff;
        position: relative;
        right: -15px
    }

    header .search .input input:focus {
        width: 300px;
        padding: 4px 23px 4px 8px;
    }

    header .search .results {
        position: absolute
    }

    header .search .results {
        right: 30px;
        width: 300px;
        text-align: left;
        background-color: #1e1e1e;
        z-index: 2;
    }

    header .search .results ul {
        width: 100%;
        list-style: none;
        margin: 0;
        padding: 0 10px;
        z-index: 2;
    }

    header .search .results ul li p {
        margin-bottom: 5px;
        cursor: pointer;
        display: block;
    }

    header .search .results ul li:last-child p {
        margin: 0;
        z-index: 2;
    }
   

</style>

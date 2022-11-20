<template>
    <header>
        <div class="logo">
            <img src="../../assets/img/logo.png" alt="logo"/>
            <p>Dacxi Tech Challenge</p>            
        </div>
        <div class="search">
            <div class="input">
                <input name="search" id="search">
                <label for="search">
                    <i class="fa-sharp fa-solid fa-magnifying-glass"></i>
                </label>                
            </div>
            
            <div class="results">

            </div>
        </div>
    </header>
</template>
<script>
export default {
    name: "CommonHeader" 
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
        height: 32px;
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
        height: 32px;
        z-index: 2;
        top: 0;
    }

    header .search .input input {
        transition: width 0.2s ease-in;
        width: 0px;
        height: 32px;
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
   

</style>

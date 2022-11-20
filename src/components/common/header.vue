<template>
    <header>
        <div class="logo">
            <p>Dacxi Tech Challenge</p>
            <img src="../../assets/img/logo.png" alt="logo"/>
        </div>
        <div class="search">f</div>
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
    }

    header > div {
        flex: 0 0 50%;
        width: 50%;
        padding: 15px;
    }

    header > div.logo img {
        width: 32px;
    }

</style>

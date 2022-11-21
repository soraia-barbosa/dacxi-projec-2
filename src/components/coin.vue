<template>
    <div>asdasd</div>
</template>
<script>
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
    mounted() {
        console.log(this.coinData);
    }
}
</script>

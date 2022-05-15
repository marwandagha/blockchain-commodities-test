<template>
    <div class="mt-5">
        <SearchBar @keyup="searchCoins($event.target.value)" />

    </div>
    <div class="row mt-custom">
        <div :key="coin.symbol" v-for="coin in coins" class="['col-12 col-lg-4 col-md-6']">

            <Coin :searchWord="searchWord" :coin="coin" />
        </div>
    </div>

    <div class="row">
        <div class="col-8 col-md-2 m-auto ">
            <LoadMoreButton @click="incrementLoader()" />
        </div>
    </div>
</template>

<script>
import Coin from './Coin'
import SearchBar from './SearchBar'
import LoadMoreButton from './LoadMoreButton'

export default {
    name: 'Coins',
    props: {
        coins: Array,
        searchWord: String,

    },
    components: {
        Coin,
        SearchBar,
        LoadMoreButton,
    },
    methods: {
        searchCoins(word) {

            this.$emit('search-coins', word)

        },
        incrementLoader() {
           
            this.$emit('increment')
        }
    },
    emits: ['search-coins', 'increment'],
}
</script>
<style scoped>
.mt-custom {
    margin-top: 4rem;
}
</style>

<template>
    <div :class="[isActive ? 'active' : '', 'coin-container']" @click="toggle()">
        <i class="far fa-coins"></i>
        <div v-if="searchWord != ''">
        </div>
        <h4 class="symbol" v-if="searchWord != ''" v-html="highlight"></h4>
        <h4 class="symbol" v-else>{{ coin.symbol }}</h4>
        <p class="mt-5">Price Change: <span :class="[coin.priceChangePercent > 0 ? 'positive' : 'negative']">{{
                coin.priceChangePercent
        }} %</span></p>
        <p class="last-price">Last Price: {{ coin.lastPrice }}</p>
        <p class="volume">Volume: {{ coin.volume }}</p>
    </div>
</template>

<script>
export default {
    name: 'Coin',
    props: {
        coin: Object,
        searchWord: String,
    },
    computed: {
        highlight: function () {

            return this.coin.symbol.replace(new RegExp(this.searchWord, "gi"), match => {
                return '<span class="highlightText">' + match + '</span>';
            });
        }
    },
    data() {
        return {
            isActive: false,

        }
    },
    methods: {
        toggle() {
            this.isActive = !this.isActive;
        }
    }
}
</script>

<style scope>
.active {
    background-color: #5a55d2 !important;
    border-color: #5a55d2 !important;
}

.coin-container {
    padding: 3rem;
    border-radius: 20px;
    margin-bottom: 2rem;
    border: solid white;
    border-width: 2px;
}

.coin-container:hover {
    cursor: pointer;
    background-color: #161616;

}

.positive {
    color: #34e334 !important;
}

.negative {
    color: #ff5151 !important;
}

.highlightText {
    background-color: #ed5d4387 !important;
}
</style>

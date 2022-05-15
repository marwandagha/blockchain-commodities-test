<template>
  <coins @increment="incrementLoader" @search-coins="searchCoins" :searchWord="searchWord" :coins="filteredCoins" />
</template>
 
 
<script>
import Coins from '../components/Coins'
import { ref } from 'vue'
export default {
  name: 'Home',
  components: {
    Coins,
  },

  async setup() {

    const allCoins = ref([]);
    const filteredCoins = ref([]);
    const searchWord = ref("");
    const loadMore = ref(1);

    //first API fetch 
    allCoins.value = await fetchCoins()

    //get first 15 coin
    filteredCoins.value = allCoins.value.slice(0, (loadMore.value * 15))

    //loadmore 15 coin with paying attention to search keyword
    async function incrementLoader() {

      loadMore.value++;

      if (searchWord != '') {
        searchCoins(searchWord.value)
      } else {
        filteredCoins.value = allCoins.value.slice(0, (loadMore.value * 15))
      }



    }


    async function fetchCoins() {

      const res = await fetch('https://api2.binance.com/api/v3/ticker/24hr')
      const data = await res.json()
      return data

    }



    async function searchCoins(word) {

      // note:
      // in real developent enviroment there should be a search API with pagination, so I should fetch the coins again. but for now I fetch only once.

      //for searched keyword highlighting
      searchWord.value = word;

      filteredCoins.value = allCoins.value.filter(d => d.symbol.toLowerCase().includes(word.toLowerCase()))
      .slice(0, (loadMore.value * 15));
  

    }

    return {

      allCoins,
      filteredCoins,
      loadMore,
      searchWord,
      fetchCoins,
      searchCoins,
      incrementLoader

    }

  }
}
</script>


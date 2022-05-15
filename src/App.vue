<template>
  <Header />
  <div class="container">
  <Suspense>
   <router-view #default></router-view>
    <template #fallback>
      <div style="color:white!important">Loading ...</div>
    </template>
  </Suspense>
  </div>
  <Footer />
</template>

<script>
import Header from './components/Header'
import Footer from './components/Footer'

export default {
  name: 'App',
  components: {
    Header,
    Footer,
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;

}

body {
  font-family: 'Poppins', sans-serif;
  background-color: black !important;
  color: white !important;
}

.container {
  min-height: 60vh;
}

.secondery-color {
  color: #5a55d2 !important;
}
</style>

<template>
  <v-app class="font-display">
    <Header />
    <Nuxt />
    <Footer /> 
  </v-app>
</template>

<script>
  import Header from '../components/Header.vue'
  import Footer from '../components/Footer.vue'

  export default {
    data () {
      return {
        clipped: false,
        drawer: false,
        fixed: false,
        items: [
          {
            icon: 'mdi-apps',
            title: 'Welcome',
            to: '/'
          },
          {
            icon: 'mdi-chart-bubble',
            title: 'Inspire',
            to: '/inspire'
          }
        ],
        miniVariant: false,
        right: true,
        rightDrawer: false,
        title: 'Vuetify.js'
      }
    }
  }
</script>
<style>
  .font-display{
    font-family: 'Poppins';
  }
</style>
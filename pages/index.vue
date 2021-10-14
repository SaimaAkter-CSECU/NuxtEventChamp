<template>
  <div>
    <Banner />
    <EventSearch />
    <UpcomingEvent />
    <EventStatus />
    <FeaturedEvent />
    <Newsletter /> 
    <Services />
    <PopularVenu />
    <LatestPost />
  </div>
</template>

<script>
  import Banner from '../components/EventSearch.vue' 
  import EventSearch from '../components/EventSearch.vue' 
  import UpcomingEvent from '../components/UpcomingEvent.vue'
  import FeaturedEvent from '../components/FeaturedEvent.vue'
  import EventStatus from '../components/EventStatus.vue'
  import Newsletter from '../components/Newsletter.vue'
  import Services from '../components/Services.vue'
  import PopularVenu from '../components/PopularVenu.vue'
  import LatestPost from '../components/LatestPost.vue'

  export default {
    // data () {
    //   return {
    //     dark: false, 
    //     clipped: false,
    //     drawer: false,
    //     fixed: false,
    //     items: [
    //       {
    //         icon: 'mdi-apps',
    //         title: 'Welcome',
    //         to: '/'
    //       },
    //       {
    //         icon: 'mdi-chart-bubble',
    //         title: 'Inspire',
    //         to: '/inspire'
    //       }
    //     ],
    //     miniVariant: false,
    //     right: true,
    //     rightDrawer: false,
    //     title: 'Vuetify.js'
    //   }
    // }
  }

</script>


<template>
  <div class="subPage">
    <SubPageBanner />
    <VenueDetail />
  </div>
</template>

<script>
    import SubPageBanner from '../../../components/SubPageBanner.vue' 
    import VenueDetail from '../../../components/VenueDetail.vue' 

    export default {
        data: () => ({

        }),
        mounted() {
          // console.log(this.$route.params.id);
          // console.log(localStorage.getItem('venueId')); 
        },
    }
</script> 
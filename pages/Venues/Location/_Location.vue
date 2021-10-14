<template>
  <div class="subPage">
    <SubPageBanner />
    <VenueLocation />
  </div>
</template>

<script>
    import SubPageBanner from '../../../components/SubPageBanner.vue' 
    import VenueLocation from '../../../components/VenueLocation.vue' 

    export default {
        data: () => ({
           
        }),
        mounted() {
            console.log(this.$route.params.Location); 
        },
    }
</script> 
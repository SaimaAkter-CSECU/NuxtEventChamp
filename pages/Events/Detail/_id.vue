<template>
  <div class="subPage">
    <SubPageBanner />
    <EventDetail />
  </div>
</template>

<script>
    import SubPageBanner from '../../../components/SubPageBanner.vue' 
    import EventDetail from '../../../components/EventDetail.vue' 

    export default {
        data: () => ({

        }),
        mounted() {
        //   console.log(this.$route.params.id);
          // console.log(localStorage.getItem('eventId')); 
        },
    }
</script> 
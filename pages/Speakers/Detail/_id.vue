<template>
  <div class="subPage">
    <SubPageBanner />
    <SpeakerDetail />
  </div>
</template>

<script>
    import SubPageBanner from '../../../components/SubPageBanner.vue' 
    import SpeakerDetail from '../../../components/SpeakerDetail.vue' 

    export default {
        data: () => ({

        }),
        mounted() {
          console.log(this.$route.params.id);
        //   console.log(localStorage.getItem('blogId')); 
        },
    }
</script> 
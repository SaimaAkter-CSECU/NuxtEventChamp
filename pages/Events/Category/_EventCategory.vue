<template>
  <div class="subPage">
    <SubPageBanner />
    <EventCategory />
  </div>
</template>

<script>
    import SubPageBanner from '../../../components/SubPageBanner.vue' ; 
    import EventCategory from '../../../components/EventCategory.vue'

    export default {
        data: () => ({
        }),
        mounted() {
          this.catName = this.$route.params.EventCategory;
        },
    }
</script> 
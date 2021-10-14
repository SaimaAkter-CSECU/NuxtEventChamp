<template>
  <div class="subPage">
    <SubPageBanner />
    <BlogCategory></BlogCategory>
  </div>
</template>

<script>
    import SubPageBanner from '../../../components/SubPageBanner.vue' 
    import BlogCategory from '../../../components/BlogCategory.vue' 

    export default {
        data: () => ({
          catName: '', 
        }),
        mounted() {
          this.catName = this.$route.params.BlogCategory;
          console.log(this.catName)
        },
    }
</script> 
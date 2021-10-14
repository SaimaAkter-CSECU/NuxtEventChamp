<template>
  <div class="subPage">
    <SubPageBanner />
    <BlogDetail />
  </div>
</template>

<script>
    import SubPageBanner from '../../../components/SubPageBanner.vue' 
    import BlogDetail from '../../../components/BlogDetail.vue' 

    export default {
        data: () => ({

        }),
        mounted() {
        //   console.log(this.$route.params.id);
          console.log(localStorage.getItem('blogId')); 
        },
    }
</script> 
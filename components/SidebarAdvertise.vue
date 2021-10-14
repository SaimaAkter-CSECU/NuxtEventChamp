<template>
    <div
        class="white advertise-div rounded-lg"
    >
        <div
            class="py-7 pl-9 text-h6"
            style="border-bottom: 1px solid #eaeaea"
        >
            Ads
        </div>
        <div
            class="pa-8"
        >
            <v-img
                :src="blogAdvertise"
                width="100%" 
            ></v-img>
        </div>
        
    </div>
</template>

<script>
    import blogAdvertise from '../assets/Images/Blog/blog-ads.png'
    export default {
        name: 'SidebarAdvertise',
        data: () => ({
            blogAdvertise: blogAdvertise, 
        }),
    }
</script>
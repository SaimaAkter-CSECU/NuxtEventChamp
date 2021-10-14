<template>
    <div class="subPageBanner">
        <v-img
            :src="SubPageBanner"
            width="100%"
            height= "285px"
        >
            <v-overlay
                width="100%"
                height="100%"
                absolute
            >
                <div 
                    class="container--fluid white--text align-center"
                >
                    <div class="text-h2 font-weight-regular">Blogs</div>
                    <div class="mt-3">
                        <span class="subtitle-2 backToHome mr-2">
                            <NuxtLink to="/">Home</NuxtLink>
                        </span>
                        <span class="mr-2"> > </span>
                        <span
                            color="yellowish"
                            class="yellowish--text subtitle-2"
                            style= "border-bottom: 2px solid #fb0"
                        >
                            Blogs
                        </span>
                    </div>
                </div>
            </v-overlay>
        </v-img>
    </div>
</template>

<script>
    import SubPageBanner from '../assets/Images/SubPageBanner.jpg' 
    export default {
        name: 'SubPageBanner',
        data: () => ({
            SubPageBanner: SubPageBanner, 
        }),
    }
</script>
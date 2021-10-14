<template>
    <section id="latestPost" class="py-9">
        <div class="container--fluid mt-9">
            <div class="section-title text-center pt-9">
                <div class="text-h3">
                    Latest <span class="yellowish--text">Posts</span>
                </div>
                <div class="section-divider d-flex align-center justify-center my-7"> 
                    <v-divider></v-divider>
                    <v-icon
                        class="mx-2"
                        
                        color="grey lighten-2"
                    >
                        mdi-view-grid-outline
                    </v-icon>
                    <v-divider></v-divider>
                </div>
                <div class="text-center mb-9">
                    <div class="subtitle-1 font-weight-regular grey--text lighten-1">
                        Lorem ipsum dolor sit amet consectetur adipiscing elit sed do eiusmod tempor.
                    </div>
                </div>
            </div>
            <div class="section-content py-9">
                <div v-swiper="swiperOption" class="w-5/6 ml-auto relative" :loadtheme="false">
                    <div class="swiper-wrapper">
                        <div class="swiper-slide" :key="latestPost.id" v-for="latestPost in latestPosts">
                            <v-card
                                elevation="0"
                                class="slider-card-div"
                            >
                                <v-img
                                    :src="latestPost.url"
                                    class="d-flex align-end rounded-lg"
                                >
                                    <NuxtLink :to="{path: 'Blogs/Category/'+(latestPost.category).charAt(0).toUpperCase()+(latestPost.category).slice(1) }">
                                        <v-btn
                                            color="white"
                                            class="yellowish--text mb-5 ml-5 rounded-pill"
                                            width="auto"
                                            min-height="32px"
                                            style="letter-spacing:0px;" 
                                            elevation="0"   
                                        >
                                            {{latestPost.category}}
                                        </v-btn>
                                    </NuxtLink>
                                </v-img>
                                <v-card-title
                                    @click="getBlog(latestPost.id)"
                                    style="cursor:pointer"
                                    class="pl-0" 
                                >
                                    <NuxtLink :to="{path: 'Events/Detail/'+(latestPost.title).split(' ').join('-')}">
                                        {{latestPost.title}}
                                    </NuxtLink>
                                </v-card-title>
                                <v-card-text
                                    class="pl-0"
                                >
                                    {{latestPost.description}}
                                </v-card-text>
                                <v-card-actions
                                    class="pl-0"
                                >
                                    <div class="mr-4">
                                        <v-icon
                                            color="yellowish"
                                            small
                                            class="mr-1"
                                        >
                                            mdi-calendar-outline
                                        </v-icon>
                                        <span class="text--primary">{{latestPost.date}}</span> 
                                    </div>
                                    <div>
                                        <v-icon
                                            color="yellowish"
                                            small
                                            class="mr-1"
                                        >
                                            mdi-chat-outline
                                        </v-icon>
                                        <span class="text--primary">{{latestPost.comment}} comment</span>
                                    </div>
                                </v-card-actions>
                            </v-card>
                        </div>
                    </div>
                    <div class="d-flex justify-center align-center mt-9">
                        <div 
                            class="swiper-button-prev btn-style py-0 px-6 rounded-lg"
                        >
                            <v-icon
                                color="grey"
                            >
                                mdi-chevron-left
                            </v-icon>
                        </div>
                        <NuxtLink to="Blogs">
                            <v-btn 
                                class="btn-style mx-5 px-6 grey--text rounded-lg"
                                elevation="0"
                            >
                                All Blog
                            </v-btn>    
                        </NuxtLink>
                        <div 
                            class="swiper-button-next btn-style py-0 px-6 rounded-lg"
                        >
                            <v-icon
                                color="grey"
                            >
                                mdi-chevron-right
                            </v-icon>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
    import { directive } from "vue-awesome-swiper";
    export default {
        name: 'LatestPost',
        data: () => ({
            latestPosts: [
                {
                    id: 1,
                    title: 'Top 20 Event and Conference Countries',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has. Sed ad dicam platonem, mea eros illum elitr id, ei has similique constituto.',
                    catId: 1, 
                    category: 'List', 
                    date: 'November 23, 2018',
                    comment: 1, 
                    url: require('../assets/Images/LatestPost/LatestPost1.png'), 
                    
                },
                {
                    id: 2,
                    title: 'Budgets for Business Events',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has. Sed ad dicam platonem, mea eros illum elitr id, ei has similique constituto.',
                    catId: 1, 
                    category: 'Events', 
                    date: 'November 23, 2018',
                    comment: 0, 
                    url: require('../assets/Images/LatestPost/LatestPost2.png'), 
                },
                {
                    id: 3,
                    title: '5 Ideas for Fun Family Activities',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has. Sed ad dicam platonem, mea eros illum elitr id, ei has similique constituto.',
                    catId: 1, 
                    category: 'List', 
                    date: 'November 23, 2018',
                    comment: 0, 
                    url: require('../assets/Images/LatestPost/LatestPost3.png'), 
                },
                {
                    id: 4,
                    title: 'Best Event Ticket Deals',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has. Sed ad dicam platonem, mea eros illum elitr id, ei has similique constituto.',
                    catId: 1, 
                    category: 'Events', 
                    date: 'November 23, 2018',
                    comment: 1, 
                    url: require('../assets/Images/LatestPost/LatestPost4.png'), 
                }
            ],
            directives: {
                swiper: directive,
            },
            swiperOption: {
                slidesPerView: 2,
                spaceBetween: 10,
                slidesPerGroup: 2,
                loop: true,
                loopFillGroupWithBlank: true,
                pagination: {
                    el: ".swiper-pagination",
                    clickable: true,
                },
                navigation: {
                    nextEl: ".swiper-button-next",
                    prevEl: ".swiper-button-prev",
                },
                breakpoints: {
                    1400:{
                        slidesPerView: 2, 
                        spaceBetween: 20, 
                    },
                    1200:{
                        slidesPerView: 2, 
                        spaceBetween: 15, 
                    },
                    1100:{
                        slidesPerView: 2, 
                        spaceBetween: 10, 
                    },
                    900:{
                        slidesPerView: 2, 
                        spaceBetween: 5, 
                    },
                    640: {
                        slidesPerView: 1,
                        spaceBetween: 0
                    }, 
                    320: {
                        slidesPerView: 1,
                        spaceBetween: 0
                    }
                }
            },
        }),
        methods:{
            async getBlog(blogId){
                localStorage.setItem("blogId", blogId); 
            }, 
        }
    }
</script>
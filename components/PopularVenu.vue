<template>
    <section id="popularVenu">
        <div class="container--fluid white--text">
            <div class="section-title text-center pb-9">
                <div class="text-h3 white--text">
                    Popular <span class="yellowish--text">Venues</span>
                </div>
                <div class="section-divider d-flex align-center justify-center my-7"> 
                    <v-divider class="grey"></v-divider>
                    <v-icon
                        class="mx-2"
                        large
                        color="grey"
                    >
                        mdi-map-legend
                    </v-icon>
                    <v-divider class="grey"></v-divider>
                </div>
                <div class="text-center mb-9">
                    <div 
                        class="subtitle-1 font-weight-regular grey--text lighten-1"
                    >
                        Lorem ipsum dolor sit amet consectetur adipiscing elit sed do eiusmod tempor.
                    </div>
                </div>
            </div>
            <div class="section-content">
                <div v-swiper="swiperOption" class="w-5/6 ml-auto relative" :loadtheme="false">
                    <div class="swiper-wrapper">
                        <div class="swiper-slide" :key="popularVenue.id" v-for="popularVenue in popularVenues">
                            <v-card
                                elevation="0"
                                class="slider-card-div white--text"
                                color="transparent"
                            >
                                <v-img
                                    :src="popularVenue.url"
                                    class="d-flex align-end rounded-lg"
                                >
                                    <NuxtLink :to="{path: 'Venues/Location/'+(popularVenue.venu).charAt(0).toUpperCase()+(popularVenue.venu).slice(1) }">
                                        <v-btn
                                            color="white"
                                            class="yellowish--text mb-5 ml-5 rounded-pill"
                                            width="auto"
                                            min-height="32px"
                                            style="letter-spacing:0px;" 
                                            elevation="0"    
                                        >
                                            {{popularVenue.venu}}
                                        </v-btn>
                                    </NuxtLink>
                                </v-img>
                                <v-card-title
                                    @click="getVenue(popularVenue.id)"
                                    style="cursor:pointer"
                                    class="font-weight-normal pl-0"
                                >
                                    <NuxtLink :to="{path: 'Venues/Detail/'+(popularVenue.title).split(' ').join('-') }">
                                        {{popularVenue.title}}
                                    </NuxtLink>
                                </v-card-title>
                                <v-card-text
                                    class="pl-0 white--text"
                                >
                                    {{popularVenue.description}}
                                </v-card-text>
                            </v-card>
                        </div>
                    </div>
                    <div class="d-flex justify-center align-center mt-9">
                        <div 
                            class="swiper-button-prev btn-style py-0 px-6 rounded-lg transparent"
                            style="border: 1px solid #eaeaea !important;"
                        >
                            <v-icon
                                color="white"
                            >
                                mdi-chevron-left
                            </v-icon>
                        </div>
                        <NuxtLink to="Venues">
                            <v-btn 
                                class="btn-style mx-5 px-6 white--text rounded-lg"
                                color="transparent"
                                style="border: 1px solid #eaeaea !important;"
                            >
                                All Venues
                            </v-btn>
                        </NuxtLink>
                        <div 
                            class="swiper-button-next btn-style py-0 px-6 rounded-lg transparent"
                            style="border: 1px solid #eaeaea !important;"
                        >
                            <v-icon
                                color="white"
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
        name: 'PopularVenu',
        data: () => ({
            popularVenues: [
                {
                    id: 1,
                    title: 'Tokyo Meeting Center',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    venuId: 1, 
                    venu: 'Tokyo', 
                    url: require('../assets/Images/Venu/venu1.png'), 
                    
                },
                {
                    id: 2,
                    title: 'London Arena',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    venuId: 2, 
                    venu: 'London', 
                    url: require('../assets/Images/Venu/venu2.png'), 
                },
                {
                    id: 3,
                    title: 'Istanbul Event Arena',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    venuId: 3, 
                    venu: 'Istanbul', 
                    url: require('../assets/Images/Venu/venu3.png'), 
                },
                {
                    id: 4,
                    title: 'Best Event Ticket Deals',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    venuId: 1, 
                    venu: 'Tokyo', 
                    url: require('../assets/Images/Venu/venu4.png'), 
                },
                {
                    id: 5,
                    title: 'Love Wedding Hall',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    venuId: 5, 
                    venu: 'California', 
                    url: require('../assets/Images/Venu/venu5.png'), 
                },
                {
                    id: 6,
                    title: 'Oxnard Beach',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    venuId: 5, 
                    venu: 'California', 
                    url: require('../assets/Images/Venu/venu6.png'), 
                }
            ],
            directives: {
                swiper: directive,
            },
            swiperOption: {
                slidesPerView: 3,
                spaceBetween: 10,
                slidesPerGroup: 3,
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
                        slidesPerView: 3, 
                        spaceBetween: 15, 
                    },
                    1200:{
                        slidesPerView: 3, 
                        spaceBetween: 10, 
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
            async getVenue(id){
                localStorage.setItem("venueId", id); 
            }, 
        }
    }
</script>
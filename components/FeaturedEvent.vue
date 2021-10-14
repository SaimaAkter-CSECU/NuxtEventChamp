<template>
    <section id="featuredEvent" class="mt-9">
        <div class="container--fluid my-9">
            <div class="section-title text-center pb-9">
                <div class="text-h3">
                    Featured <span class="yellowish--text">Events</span>
                </div>
                <div class="section-divider d-flex align-center justify-center my-9"> 
                    <v-divider></v-divider>
                    <v-icon
                        class="mx-2"
                        
                        color="grey lighten-2"
                    >
                        mdi-license
                    </v-icon>
                    <v-divider></v-divider>
                </div>
                <div class="text-center mb-9">
                    <div class="subtitle-1 font-weight-regular grey--text lighten-1">
                        Lorem ipsum dolor sit amet consectetur adipiscing elit sed do eiusmod tempor.
                    </div>
                </div>
            </div>
            <div class="section-content">
                <div v-swiper="swiperOption" class="w-5/6 ml-auto relative" :loadtheme="false">
                    <div class="swiper-wrapper">
                        <div class="swiper-slide" :key="featuredEvent.id" v-for="featuredEvent in featuredEvents">
                            <v-card class="slider-card-div">
                                <NuxtLink :to="{path: 'Events/Detail/'+(featuredEvent.title).split(' ').join('-')}">
                                    <v-img
                                        :src="featuredEvent.url"
                                        @click="getEvent(featuredEvent.id)"
                                        style="cursor:pointer; max-height: 391px; "
                                        
                                    >
                                        <div
                                            v-show="featuredEvent.discount"
                                            class="body-2 yellowish--text discount-div"
                                            background-color="white"
                                            style="cursor: default"
                                        >
                                            Discount
                                        </div>
                                    </v-img>
                                </NuxtLink>
                                <v-card-title
                                    @click="getEvent(featuredEvent.id)"
                                    style="cursor:pointer"
                                >
                                    <NuxtLink :to="{path: 'Events/Detail/'+(featuredEvent.title).split(' ').join('-')}">
                                        {{featuredEvent.title}}
                                    </NuxtLink>
                                </v-card-title>
                                <v-card-actions
                                    class="px-4"
                                >
                                    <v-btn
                                        class="white--text rounded-pill px-4"
                                        color="yellowish" 
                                        width="auto"
                                        min-height="32px"
                                        style="letter-spacing:0px;" 
                                        elevation="0" 
                                    >
                                        <NuxtLink :to="{path: 'Events/Category/'+(featuredEvent.category).charAt(0).toUpperCase()+(featuredEvent.category).slice(1) }">
                                            {{featuredEvent.category}}
                                        </NuxtLink>
                                    </v-btn>
                                    <div class="ml-7">
                                        <v-icon
                                            color="yellowish"
                                            small
                                            class="mr-1"
                                        >
                                            mdi-calendar-outline
                                        </v-icon>
                                        <span class="text--secondary">{{featuredEvent.date}}</span> 
                                    </div>
                                </v-card-actions>
                                <v-card-text
                                    class="px-4"
                                >
                                    {{featuredEvent.description}}
                                </v-card-text>
                                <v-card-actions
                                    class="px-4 pb-7"
                                >
                                    <div class="mr-4">
                                        <v-icon
                                            color="yellowish"
                                            small
                                            class="mr-1"
                                        >
                                            mdi-timer-sand
                                        </v-icon>
                                        <span class="text--secondary">{{featuredEvent.eventStatus}}</span> 
                                    </div>
                                    <div class="mr-4">
                                        <v-icon
                                            color="yellowish"
                                            small
                                            class="mr-1"
                                        >
                                            mdi-map-marker-outline
                                        </v-icon>
                                        <span 
                                            class="text--secondary"
                                        >
                                            <NuxtLink :to="{path: 'Venues/Location/'+(featuredEvent.location).charAt(0).toUpperCase()+(featuredEvent.location).slice(1) }">
                                                {{featuredEvent.location}}
                                            </NuxtLink>
                                        </span>
                                    </div>
                                    <div>
                                        <v-icon
                                            color="yellowish"
                                            small
                                            class="mr-1"
                                        >
                                            mdi-cash
                                        </v-icon>
                                        <span class="text--secondary">
                                            <span v-if=" !(featuredEvent.cost == 'Free') "> $</span>
                                            {{featuredEvent.cost}}
                                        </span>
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
                        <NuxtLink to="Events">
                            <v-btn 
                                class="btn-style mx-5 px-6 grey--text rounded-lg"
                                elevation="0"
                            >
                                All Events
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
        name: "FeaturedEvent",
        data: () => ({
            featuredEvents: [
                {
                    id: 1,
                    title: 'Megeve Winter Party',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    catId: 1, 
                    category: 'Travel', 
                    date: 'January 17, 2022',
                    eventStatus: 'Upcomming', 
                    location: 'Megeve', 
                    cost: '150', 
                    discount: false,
                    url: require('../assets/Images/LatestPost/LatestPost1.png'), 
                },
                {
                    id: 2,
                    title: 'Wedding of James & Helen',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    catId: 2, 
                    category: 'Wedding', 
                    date: 'August 21, 2022',
                    eventStatus: 'Showing', 
                    location: 'California', 
                    cost: 'Free', 
                    discount: true,
                    url: require('../assets/Images/LatestPost/LatestPost1.png'), 
                },
                {
                    id: 3,
                    title: 'Rock Concert of the Gloria',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    catId: 3, 
                    category: 'Technology', 
                    date: 'July 22, 2022',
                    eventStatus: 'Upcomming', 
                    location: 'Paris', 
                    cost: '99', 
                    discount: false,
                    url: require('../assets/Images/LatestPost/LatestPost1.png'), 
                },
                {
                    id: 4,
                    title: 'Eventchamp Conference',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    catId: 4, 
                    category: 'Business', 
                    date: 'March 21, 2021',
                    eventStatus: 'Showing', 
                    location: 'London', 
                    cost: '149', 
                    discount: false,
                    url: require('../assets/Images/LatestPost/LatestPost1.png'), 
                },
                {
                    id: 5,
                    title: 'Eventchamp Conference',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    catId: 5, 
                    category: 'NightLife', 
                    date: 'March 21, 2022',
                    eventStatus: 'Upcomming', 
                    location: 'New Work', 
                    cost: '70', 
                    discount: true,
                    url: require('../assets/Images/LatestPost/LatestPost1.png'), 
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
                        spaceBetween: 10, 
                    },
                    1200:{
                        slidesPerView: 3, 
                        spaceBetween: 10, 
                    },
                    1100:{
                        slidesPerView: 3, 
                        spaceBetween: 5, 
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
            async getEvent(id){
                localStorage.setItem("eventId", id);
            }, 
            // async getVenue(venueId){
            //     localStorage.setItem("venueId", venueId);
            // }, 
        }
    }
</script>
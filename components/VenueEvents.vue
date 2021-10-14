<template>
    <section class="my-9">
        <div class="container--fluid">
            <div class="section-title text-center">
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
                        You might also love these events.
                    </div>
                </div>
            </div>
            <div class="section-content">
                <v-row>
                    <v-col
                        col="12"
                        md="4"
                        sm="6"
                        xs="12"
                        v-for="event in events"
                        :key="event.id"
                    >
                        <v-card 
                            card="rounded-lg"
                            style="border: 1px solid #eaeaea"
                            elevation="0"
                        >
                            <v-img
                                :src="event.url"
                                style="max-height: 391px; "   
                            >
                            </v-img>
                            <v-card-title
                                @click="geTEvent(event.id)"
                            >
                                <NuxtLink :to="{path: '../../Events/Detail/'+(event.title).split(' ').join('-') }">
                                    {{event.title}}
                                </NuxtLink>
                            </v-card-title>
                            <v-card-actions
                                class="px-4"
                            >
                                <v-btn
                                    class="white--text rounded-pill px-4"
                                    elevation="0"
                                    color="yellowish" 
                                    style="letter-spacing:0.25px" 
                                >
                                    <NuxtLink :to="{path: '../../Events/Category/'+(event.category).charAt(0).toUpperCase()+(event.category).slice(1) }">
                                        {{event.category}}
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
                                    <span class="text--secondary">{{event.date}}</span> 
                                </div>
                            </v-card-actions>
                            <v-card-text
                                class="px-4"
                            >
                                {{event.description}}
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
                                    <span class="text--secondary">{{event.eventStatus}}</span> 
                                </div>
                                <div class="mr-4">
                                    <v-icon
                                        color="yellowish"
                                        small
                                        class="mr-1"
                                    >
                                        mdi-map-marker-outline
                                    </v-icon>
                                    <span class="text--secondary">{{event.location}}</span>
                                </div>
                            </v-card-actions>
                        </v-card>
                    </v-col>
                </v-row>
            </div>
        </div>
    </section>
</template>
<script>
    export default {
        name: "VenueEvents",
        data: () => ({
            events: [
                {
                    id: 1,
                    title: 'Megeve Winter Party',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    catId: 1, 
                    category: 'Travel', 
                    date: 'January 17, 2022',
                    eventStatus: 'Upcomming', 
                    location: 'Megeve', 
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
                    url: require('../assets/Images/LatestPost/LatestPost1.png'), 
                },
                
            ],
        }),
        methods:{
            async goToEvent(id){
                console.log(id); 
            }, 
            async goToVenuCategory(id){
                console.log(id); 
            }
        }
    }
</script>
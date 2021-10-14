<template>
    <div class="subPageContent">
        <div class="container--fluid">
            <v-row>
                <v-col
                    col="12"
                    md="8"
                    sm="12"
                >
                    <div 
                        class="white content-div pa-8 rounded-lg"
                    >
                        <v-row>
                            <v-col
                                sm="6"
                                xs="12"
                                v-for="venue in filterVenues"
                                :key="venue.id"
                            >
                                <v-card
                                    elevation="0"
                                >
                                    <v-img
                                        :src="venue.url"
                                        class= "rounded-lg"
                                        width="100%"
                                    >
                                        <div
                                            class="d-flex align-end pa-7"
                                            style="width:100%; height: 100%;"
                                        >
                                            <NuxtLink :to="{path: 'Venues/Location/'+venue.venue}">
                                                <v-btn
                                                    class="rounded-pill yellowish--text text-uppercase" 
                                                    color="white"
                                                    style="font-weight: 400; letter-spacing: 0.25px"
                                                >
                                                    {{venue.venue}}
                                                </v-btn>
                                            </NuxtLink>
                                        </div>
                                    </v-img>
                                    <v-card-title
                                        class="px-0 pb-0 d-inline-block text-truncate"
                                        style="max-width: 100%"
                                        @click="getVenue(venue.id)"
                                    >
                                        <NuxtLink :to="{path: '../../Venues/Detail/'+(venue.title).split(' ').join('-') }">
                                            {{venue.title}}
                                        </NuxtLink>
                                    </v-card-title>
                                    <v-card-text
                                        class="px-0 pt-2 pb-4 gray--text darken-3 text-justify"
                                    >
                                        {{venue.description}}
                                    </v-card-text>
                                </v-card>
                            </v-col>
                        </v-row>
                    </div>
                </v-col>
                <v-col
                    col="12"
                    md="4"
                    sm="12"
                >
                    <SidebarAdvertise /> 
                </v-col>
            </v-row>
        </div>
    </div>
</template>

<script>
    import SidebarAdvertise from '../components/SidebarAdvertise.vue'
    export default {
        name: 'VenueLocation',
        data: () => ({
            venues: [
                {
                    id: 1,
                    title: 'Tokyo Meeting Center',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    venueId: 1, 
                    venue: 'Tokyo', 
                    url: require('../assets/Images/Venu/venu1.png'), 
                    
                },
                {
                    id: 2,
                    title: 'London Arena',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    venueId: 2, 
                    venue: 'London', 
                    url: require('../assets/Images/Venu/venu2.png'), 
                },
                {
                    id: 3,
                    title: 'Istanbul Event Arena',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    venueId: 3, 
                    venue: 'Istanbul', 
                    url: require('../assets/Images/Venu/venu3.png'), 
                },
                {
                    id: 4,
                    title: 'Best Event Ticket Deals',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    venueId: 1, 
                    venue: 'Tokyo', 
                    url: require('../assets/Images/Venu/venu4.png'), 
                },
                {
                    id: 5,
                    title: 'Love Wedding Hall',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    venueId: 5, 
                    venue: 'California', 
                    url: require('../assets/Images/Venu/venu5.png'), 
                },
                {
                    id: 6,
                    title: 'Oxnard Beach',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    venuId: 5, 
                    venue: 'California', 
                    url: require('../assets/Images/Venu/venu6.png'), 
                },
                {
                    id: 7,
                    title: 'Oxnard Beach 2',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    venuId: 5, 
                    venue: 'California', 
                    url: require('../assets/Images/Venu/venu6.png'), 
                }
            ],
            filterVenues: [], 
        }), 
        methods: {
            async getVenue(id){
                localStorage.setItem("venueId", id);
                console.log(localStorage); 
            },
        },
        mounted(){
            // console.log(this.$route.params.Location.toLowerCase());
            this.filterVenues = (this.venues).filter(x => x.venue.toLowerCase() === this.$route.params.Location.toLowerCase()); 
            // console.log(this.filterVenues)
        }
    }
</script>
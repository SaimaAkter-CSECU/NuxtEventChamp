<template>
    <div class="subPageContent">
        <div class="container--fluid">
            <v-row
                class="content-div"
            >
                <v-col
                    col="12"
                    md="4"
                    sm="6"
                    xs="12"
                    v-for="venue in venues"
                    :key="venue.id"
                >
                    <v-card
                        elevation="0"
                        class=""
                    >
                        <v-img
                            :src="venue.url"
                            style="cursor:pointer; max-height: 391px; "
                            class="d-flex align-end rounded-lg"
                        >
                            <NuxtLink :to="{path: 'Venues/Location/'+(venue.venue) }">
                                <v-btn
                                    color="white"
                                    class="yellowish--text font-weight-normal mb-5 ml-5 rounded-pill"
                                    height="40px"
                                    style="letter-spacing: 0.25px;"
                                >
                                    {{venue.venue}}
                                </v-btn>
                            </NuxtLink>
                        </v-img>
                        <v-card-title
                            @click="getVenue(venue.id)"
                            class="px-0 pb-0 d-inline-block text-truncate"
                            style="max-width: 100%"
                        >
                            <NuxtLink :to="{path: 'Venues/Detail/'+(venue.title).split(' ').join('-') }">
                                {{venue.title}}
                            </NuxtLink> 
                        </v-card-title>
                        <v-card-text
                            class="px-0 grey--text"
                        >
                            {{venue.description}}
                        </v-card-text>
                    </v-card>
                </v-col>
            </v-row>
        </div>     
    </div>
</template>

<script>
    export default {
        name: 'Venues',
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
                }
            ],
        }),
        methods:{
            async getVenue(id){
                localStorage.setItem("venueId", id);
                console.log(localStorage);
            }
        }
    }
</script>
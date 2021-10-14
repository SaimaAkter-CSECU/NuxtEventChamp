<template>
    <section>
        <div class="section-title text-center">
            <div class="text-h3">
                Related <span class="yellowish--text font-weight-medium">Venues</span>
            </div>
            <div class="section-divider d-flex align-center justify-center my-9"> 
                <v-divider
                    style="max-width: 150px !important; width: 150px !important"
                ></v-divider>
                <v-icon
                    class="mx-2"
                    
                    color="grey lighten-2"
                >
                    mdi-map-legend
                </v-icon>
                <v-divider
                    style="max-width: 150px !important; width: 150px !important"
                ></v-divider>
            </div>
            <div class="text-center mb-9">
                <div class="text-p font-weight-normal grey--text lighten-1">
                    You might also love these venues.
                </div>
            </div>
        </div>
        <div class="section-content py-9">
            <v-row>
                <v-col
                    col="12"
                    md="4"
                    sm="6"
                    xs="12"
                    v-for="venue in venues"
                    :key="venue.id"
                >
                    <v-card
                        class="rounded-md" 
                        elevation="0"
                        color="transparent"
                    >
                        <NuxtLink to="/">
                            <v-img
                                :src="venue.url"
                                style="border-top-left-radius: 4px; border-top-right-radius: 4px;"
                            >
                                <div
                                    style="width:100%; height: 100%"
                                    class="d-flex align-end pa-7"
                                >
                                    <NuxtLink :to="{path: '../../Venues/Location/'+(venue.venue).charAt(0).toUpperCase()+(venue.venue).slice(1) }">
                                        <v-btn
                                            class="yellowish--text px-4 rounded-pill"
                                            width="auto"
                                            min-height="32px"
                                            color="white"
                                            style="letter-spacing:0px;" 
                                            elevation="0" 
                                        >
                                            {{venue.venue}}
                                        </v-btn>
                                    </NuxtLink>
                                </div>
                            </v-img>
                        </NuxtLink>
                        <div class="py-8 px-1">
                            <v-card-title
                                class="pa-0 mb-3"
                            >
                                <NuxtLink :to="{path: '../../Venues/Detail/'+(venue.title).split(' ').join('-')}">
                                    {{venue.title}}
                                </NuxtLink>
                            </v-card-title>
                            <v-card-text
                                class="px-0 body-2 grey--text text-justify"
                            >
                                {{venue.description}}
                            </v-card-text>                           
                        </div>
                    </v-card>
                </v-col>
            </v-row>
        </div>
    </section>
</template>

<script>
    export default {
        name: 'RelatedVenues', 
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
            ]
        }),
    }
</script>
<template>
    <div>
        <div class="section-title text-center">
                <div class="text-md-h3 text-sm-h5 font-weight-bold">
                    Events of the Speaker
                </div>
                <div class="section-divider d-flex align-center justify-center my-9"> 
                    <v-divider
                        style="max-width: 150px !important; width: 150px !important"
                    ></v-divider>
                    <v-icon
                        class="mx-2"
                        
                        color="grey lighten-2"
                    >
                        mdi-calendar-month-outline
                    </v-icon>
                    <v-divider
                        style="max-width: 150px !important; width: 150px !important"
                    ></v-divider>
                </div>
                <div class="text-center mb-9">
                    <div class="text-p font-weight-normal grey--text lighten-1">
                        You might also love these events.
                    </div>
                </div>
            </div>
            <div class="section-content py-9">
                <v-row
                    class="content-div"
                >
                    <v-col
                        col="12"
                        md="4"
                        sm="6"
                        xs="12"
                        v-for="event in events"
                        :key="event.id"
                    >
                        <v-card
                            class="rounded-md" 
                            style="border: 1px solid #eaeaea" 
                            elevation="0"
                        >
                            <NuxtLink :to="{path: '../../Events/Detail/'+(event.title).split(' ').join('-')}">
                                <v-img
                                    :src="event.url"
                                    style="border-top-left-radius: 4px; border-top-right-radius: 4px;"
                                >
                                </v-img>
                            </NuxtLink>
                            <div class="py-8 px-7">
                                <v-card-title
                                    class="pa-0 mb-4"
                                >
                                    <NuxtLink :to="{path: '../../Events/Detail/'+(event.title).split(' ').join('-')}">
                                        {{event.title}}
                                    </NuxtLink>
                                </v-card-title>
                                <div
                                    class="d-flex flex-wrap pa-0"
                                >
                                    <NuxtLink :to="{path: 'Events/Category/'+(event.category).charAt(0).toUpperCase()+(event.category).slice(1) }">
                                        <v-btn
                                            class="white--text px-4 rounded-pill mr-5"
                                            width="auto"
                                            min-height="32px"
                                            color="yellowish"
                                            style="letter-spacing:0px;" 
                                            elevation="0" 
                                        >
                                            {{event.category}}
                                        </v-btn>
                                    </NuxtLink>

                                    <span class="d-flex align-center mx-3 py-2">
                                        <v-icon
                                            color="yellowish"
                                            small
                                        >
                                            mdi-calendar-blank-outline
                                        </v-icon>
                                        <span class="text--secondary ml-2">{{event.date}}</span>
                                    </span>
                                </div>
                                <v-card-text
                                    class="px-0 body-2 grey--text text-justify"
                                >
                                    {{event.description}}
                                </v-card-text>
                                <v-card-text
                                    class="pa-0"
                                >
                                    <div
                                        class="d-flex flex-wrap pa-0"
                                    >
                                        <span class="d-flex align-center mr-5">
                                            <v-icon
                                                color="yellowish"
                                            >
                                                mdi-timer-sand
                                            </v-icon>
                                            <span class="grey--text ml-1">{{event.status}}</span>
                                        </span>
                                        <span class="d-flex align-center mr-5">
                                            <v-icon
                                                color="yellowish"
                                            >
                                                mdi-map-marker-outline
                                            </v-icon>
                                            <span class="grey--text ml-1">{{event.location}}</span>
                                        </span>

                                        <span class="d-flex align-center">
                                            <v-icon
                                                color="yellowish"
                                            >
                                                mdi-cash
                                            </v-icon>
                                            <span class="grey--text ml-1">
                                                <span v-show="!(event.cost == 'Free')">$</span> 
                                                {{event.cost}}
                                            </span>
                                        </span>

                                    </div>
                                </v-card-text>                                
                            </div>
                        </v-card>
                    </v-col>
                </v-row>
            </div>
    </div>
</template>

<script>
    export default {
        name: 'SpeakerEvents', 
        data: () => ({
            events: [
                {
                    id: 1, 
                    title: 'Milano 21T Meeting', 
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    status: 'Showing', 
                    date: '21 November, 2021', 
                    location: 'Milano', 
                    catId: 2,
                    category: 'Business', 
                    cost: '29', 
                    url: require('../assets/Images/LatestPost/LatestPost1.png')
                },
                {
                    id: 2, 
                    title: 'Gaming X2021 Fair', 
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    status: 'Showing', 
                    date: '21 September, 2021', 
                    location: 'Istambul', 
                    catId: 11,
                    category: 'Technology', 
                    cost: '75', 
                    url: require('../assets/Images/LatestPost/LatestPost2.png')
                },
                {
                    id: 3, 
                    title: 'Eventchamp Conference', 
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    status: 'Showing', 
                    date: 'March 12, 2021', 
                    location: 'Istambul', 
                    catId: 2,
                    category: 'Business', 
                    cost: '149', 
                    url: require('../assets/Images/LatestPost/LatestPost3.png')
                },
            ]
        }),
    }
</script>
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
                                col="12"
                                md="6"
                                sm="6"
                                xs="12" 
                                v-for="event in filterevents"
                                :key="event.id"
                            >
                                <v-card
                                    elevation="0"
                                >
                                    <v-img
                                        :src="event.url"
                                        class="pa-4 rounded-lg"
                                    >
                                        <div
                                            class="d-flex justify-space-between align-end"
                                            style="height: 100%"
                                        >
                                            <v-btn
                                                class="yellowish--text px-4 rounded-pill"
                                                width="auto"
                                                min-height="32px"
                                                color="white"
                                                style="letter-spacing:0px; cursor: default;" 
                                                elevation="0" 
                                            >
                                                {{event.status}}
                                            </v-btn>
                                            <v-btn
                                                class="white--text px-4 rounded-pill"
                                                color="yellowish"
                                                width="auto"
                                                min-height="32px"
                                                style="letter-spacing:0px; cursor: default;" 
                                                elevation="0"
                                                
                                            >
                                                <span v-show="!(event.cost == 'Free')">$</span> 
                                                {{event.cost}}
                                            </v-btn>
                                        </div>
                                    </v-img>
                                    <v-card-title
                                        class="px-0"
                                        @click="geTEvent(event.id)"
                                    >
                                        <NuxtLink :to="{path: '../../Events/Detail/'+(event.title).split(' ').join('-') }">
                                            {{event.title}}
                                        </NuxtLink>
                                    </v-card-title>
                                    <div
                                        class="d-flex flex-wrap pl-0"
                                    >
                                        <NuxtLink :to="{path: '../../Events/Category/'+(event.category).charAt(0).toUpperCase()+(event.category).slice(1) }">
                                            <v-btn
                                                class="white--text px-4 rounded-pill mr-4"
                                                width="auto"
                                                min-height="32px"
                                                color="yellowish"
                                                style="letter-spacing:0px;" 
                                                elevation="0" 
                                            >
                                                {{event.category}}
                                            </v-btn>
                                        </NuxtLink>

                                        <span class="d-flex align-center mr-4 py-2">
                                            <v-icon
                                                color="yellowish"
                                                small
                                            >
                                                mdi-calendar-blank-outline
                                            </v-icon>
                                            <span class="grey--text ml-1">{{event.date}}</span>
                                        </span>

                                        <span class="d-flex align-center py-2">
                                            <v-icon
                                                color="yellowish"
                                            >
                                                mdi-map-marker-outline
                                            </v-icon>
                                            <span class="grey--text ml-1">{{event.location}}</span>
                                        </span>

                                    </div>
                                    <v-card-text
                                        class="px-0 grey--text text-justify"
                                    >
                                        {{event.description}}
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
    import SidebarAdvertise from './SidebarAdvertise.vue'
    export default {
        name: 'EventCategory',
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
                {
                    id: 4, 
                    title: 'The Future of Currencies', 
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    status: 'Showing', 
                    date: 'July 17, 2021', 
                    location: 'Milan', 
                    catId: 11,
                    category: 'Technology', 
                    cost: '299', 
                    url: require('../assets/Images/LatestPost/LatestPost4.png')
                },
                {
                    id: 5, 
                    title: 'Wedding of James & Helen',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    status: 'Showing', 
                    date: 'August 20, 2021', 
                    location: 'California', 
                    catId: 13,
                    category: 'WEDDING', 
                    cost: 'Free', 
                    url: require('../assets/Images/LatestPost/LatestPost4.png')
                },
                {
                    id: 6, 
                    title: 'Travel Tour', 
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    status: 'Showing', 
                    date: '21 November, 2021', 
                    location: 'Milano', 
                    catId: 12,
                    category: 'Travel', 
                    cost: '29', 
                    url: require('../assets/Images/LatestPost/LatestPost1.png')
                },
                {
                    id: 7, 
                    title: 'Gaming X2021 Fair', 
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    status: 'Upcoming', 
                    date: '21 September, 2021', 
                    location: 'Istambul', 
                    catId: 10,
                    category: 'Sports', 
                    cost: '75', 
                    url: require('../assets/Images/LatestPost/LatestPost2.png')
                },
                {
                    id: 8, 
                    title: 'Eventchamp Party', 
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    status: 'Showing', 
                    date: 'March 12, 2021', 
                    location: 'Istambul', 
                    catId: 9,
                    category: 'Nightlife', 
                    cost: 'Free', 
                    url: require('../assets/Images/LatestPost/LatestPost3.png')
                },
                {
                    id: 9, 
                    title: 'The Future of Currencies', 
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    status: 'Expired', 
                    date: 'July 17, 2021', 
                    location: 'Milan', 
                    catId: 8,
                    category: 'Micellaneous', 
                    cost: '299', 
                    url: require('../assets/Images/LatestPost/LatestPost4.png')
                },
                {
                    id: 10, 
                    title: 'Wedding of James & Helen',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    status: 'Expired', 
                    date: 'August 20, 2021', 
                    location: 'California', 
                    catId: 13,
                    category: 'WEDDING', 
                    cost: 'Free', 
                    url: require('../assets/Images/LatestPost/LatestPost4.png')
                },
                {
                    id: 11, 
                    title: 'Food carnival', 
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    status: 'Showing', 
                    date: '21 November, 2021', 
                    location: 'Milano', 
                    catId: 7,
                    category: 'Food', 
                    cost: '29', 
                    url: require('../assets/Images/LatestPost/LatestPost1.png')
                },
                {
                    id: 12, 
                    title: 'Gaming X2021 Fair', 
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    status: 'Upcoming', 
                    date: '21 September, 2021', 
                    location: 'Istambul', 
                    catId: 6,
                    category: 'Festival', 
                    cost: '75', 
                    url: require('../assets/Images/LatestPost/LatestPost2.png')
                },
                {
                    id: 13, 
                    title: 'Eventchamp Education', 
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    status: 'Showing', 
                    date: 'March 12, 2021', 
                    location: 'Istambul', 
                    catId: 5,
                    category: 'Education', 
                    cost: '149', 
                    url: require('../assets/Images/LatestPost/LatestPost3.png')
                },
                {
                    id: 14, 
                    title: 'The Future of Currencies', 
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    status: 'Showing', 
                    date: 'July 17, 2021', 
                    location: 'Milan', 
                    catId: 4,
                    category: 'Conferrence', 
                    cost: '299', 
                    url: require('../assets/Images/LatestPost/LatestPost4.png')
                },
                {
                    id: 15, 
                    title: 'Concert of James & Helen',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    status: 'Expired', 
                    date: 'August 20, 2021', 
                    location: 'California', 
                    catId: 3,
                    category: 'Concert', 
                    cost: '75', 
                    url: require('../assets/Images/LatestPost/LatestPost4.png')
                },
                {
                    id: 16, 
                    title: 'Concert of James & Helen',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    status: 'Expired', 
                    date: 'August 20, 2021', 
                    location: 'California', 
                    catId: 1,
                    category: 'Art', 
                    cost: '75', 
                    url: require('../assets/Images/LatestPost/LatestPost4.png')
                },
                {
                    id: 17, 
                    title: 'Drama Games 2021',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has.',
                    status: 'Upcoming', 
                    date: 'October 10, 2021', 
                    location: 'Helsink', 
                    catId: 1,
                    category: 'Art', 
                    cost: '39', 
                    url: require('../assets/Images/LatestPost/LatestPost4.png')
                },
            ],
            filterevents: [], 
        }), 
        methods: {
            async geTEvent(id){
                localStorage.setItem("eventId", id);
                console.log(localStorage); 
            },
        },
        mounted(){
            console.log(this.$route.params.EventCategory); 
            this.filterevents = (this.events).filter(x => x.category.toLowerCase() === this.$route.params.EventCategory.toLowerCase()); 
        }
    }
</script>
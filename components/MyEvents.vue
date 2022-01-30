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
                                sm="12"
                                v-for="event in events"
                                :key="event.id"
                            >
                                <v-card
                                    elevation="0"
                                >
                                    <v-img
                                        :src="event.url"
                                        class= "rounded-lg"
                                        width="100%"
                                        height= "491px"
                                        style="cursor:pointer;"
                                    >
                                        <div
                                            class="d-flex align-end justify-space-between pa-7"
                                            style="width:100%; height: 100%;"
                                        >
                                            <NuxtLink :to="{path: '../Events/Category/'+(event.category).charAt(0).toUpperCase()+(event.category).slice(1) }">
                                                <v-btn
                                                    class="rounded-pill yellowish--text text-uppercase" 
                                                    color="white"
                                                    style="font-weight: 400; letter-spacing: 0.25px"
                                                >
                                                    {{event.category}}
                                                </v-btn>
                                            </NuxtLink>
                                            <v-btn
                                                class="rounded-pill white--text" 
                                                color="yellowish"
                                                style="cursor: default; font-weight: 400; letter-spacing: 0.25px"
                                            >
                                                {{event.acceptanceStatus}}
                                            </v-btn>
                                        </div>
                                    </v-img>
                                    <v-card-title
                                        class="px-0 pb-0 d-inline-block text-truncate"
                                        style="max-width: 100%"
                                        @click="geTEvent(event.id)"
                                    >
                                        <NuxtLink :to="{path: '../../Events/Detail/'+(event.title).split(' ').join('-') }">
                                            {{event.title}}
                                        </NuxtLink>
                                    </v-card-title>
                                    <v-card-text
                                        class="px-0 pt-2 pb-4 gray--text darken-3 text-justify"
                                    >
                                        {{event.description}}
                                    </v-card-text>
                                    <v-card-text
                                        class="px-0 pt-0 mb-3"
                                    >
                                        <div class="d-flex align-center justify-space-between align-center">
                                            <div class="d-flex align-center">
                                                <div
                                                    class="mr-5 d-flex align-center"
                                                >
                                                    <v-icon
                                                        color="yellowish"
                                                        small
                                                        class="mr-2"
                                                    >
                                                        mdi-timer-sand
                                                    </v-icon>
                                                    <span class="body-2">
                                                        {{event.status}}
                                                    </span>
                                                </div>
                                                <div
                                                    class="mr-5 d-flex align-center"
                                                >
                                                    <v-icon
                                                        color="yellowish"
                                                        small
                                                        class="mr-2"
                                                    >
                                                        mdi-map-marker-outline
                                                    </v-icon>
                                                    <span class="body-2">
                                                        {{event.location}}
                                                    </span>
                                                </div>
                                                <div
                                                    class="d-flex align-center"
                                                >
                                                    <v-icon
                                                        color="yellowish"
                                                        small
                                                        class="mr-2"
                                                    >
                                                        mdi-calendar-blank-outline
                                                    </v-icon>
                                                    <span class="body-2">
                                                        {{event.date}} 
                                                    </span>
                                                </div>
                                            </div>
                                            <NuxtLink :to="{path: '../../Events/Detail/'+(event.title).split(' ').join('-') }">
                                                <v-btn
                                                    color="yellowish"
                                                    class="white--text rounded-pill px-8 py-6 btn-style"
                                                    Height="40px"
                                                    min-width="64px"
                                                    @click="geTEvent(event.id)"
                                                >
                                                    Read More
                                                </v-btn>
                                            </NuxtLink>
                                        </div>
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
        name: 'MyEvents',
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
                    url: require('../assets/Images/LatestPost/LatestPost1.png'),
                    acceptanceStatus: 'Pending',
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
                    url: require('../assets/Images/LatestPost/LatestPost2.png'),
                    acceptanceStatus: 'Approved',
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
                    url: require('../assets/Images/LatestPost/LatestPost3.png'),
                    acceptanceStatus: 'Declined',
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
                    url: require('../assets/Images/LatestPost/LatestPost4.png'),
                    acceptanceStatus: 'Pending',
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
                    url: require('../assets/Images/LatestPost/LatestPost4.png'),
                    acceptanceStatus: 'Pending',
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
                    url: require('../assets/Images/LatestPost/LatestPost1.png'),
                    acceptanceStatus: 'Approved',
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
                    url: require('../assets/Images/LatestPost/LatestPost2.png'),
                    acceptanceStatus: 'Approved',
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
                    url: require('../assets/Images/LatestPost/LatestPost3.png'),
                    acceptanceStatus: 'Pending',
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
                    url: require('../assets/Images/LatestPost/LatestPost4.png'),
                    acceptanceStatus: 'Pending',
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
                    url: require('../assets/Images/LatestPost/LatestPost4.png'),
                    acceptanceStatus: 'Pending',
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
                    url: require('../assets/Images/LatestPost/LatestPost1.png'),
                    acceptanceStatus: 'Approved',
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
                    url: require('../assets/Images/LatestPost/LatestPost2.png'),
                    acceptanceStatus: 'Pending',
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
                    url: require('../assets/Images/LatestPost/LatestPost3.png'),
                    acceptanceStatus: 'Pending',
                },
            ],
        }), 
        methods: {
            async geTEvent(id){
                localStorage.setItem("eventId", id);
                console.log(localStorage); 
            },
        },
        
    }
</script>
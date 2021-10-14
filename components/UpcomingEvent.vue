<template>
    <section id="upcomingEvent" class="py-9">
        <div class="container--fluid my-9">
            <div class="section-title text-center pt-9">
                <div class="text-h3">
                    Upcoming <span class="yellowish--text">Events</span>
                </div>
                <div class="section-divider d-flex align-center justify-center my-9"> 
                    <v-divider></v-divider>
                    <v-icon
                        class="mx-2"
                        
                        color="grey lighten-2"
                    >
                        mdi-calendar-blank-outline
                    </v-icon>
                    <v-divider></v-divider>
                </div>
                <div class="text-center mb-9">
                    <div class="subtitle-1 font-weight-regular grey--text lighten-1">
                        Lorem ipsum dolor sit amet consectetur adipiscing elit sed do eiusmod tempor.
                    </div>
                </div>
            </div>
            <div class="section-content pb-9">
                <div class="d-flex justify-center align-center my-9 py-9 filters">
                    <v-btn-toggle
                        v-model="toggle_one"
                        mandatory
                    >
                        <v-btn
                            class="white--text rounded-pill px-4 mx-1"
                            color="yellowish"
                            width="auto"
                            min-height="32px"
                            style="letter-spacing:0px;" 
                            elevation="0" 
                            @click="changeContent(0)"
                        >
                            All
                        </v-btn>
                        <v-btn
                            class="white--text rounded-pill px-5 py-2 mx-1"
                            color="yellowish"
                            width="auto"
                            min-height="32px"
                            style="letter-spacing:0px;" 
                            elevation="0"
                            @click="changeContent(category.id)"
                            v-for="category in listCategory"
                            :key="category.id"
                        >
                            {{category.cat}}
                        </v-btn>
                        <v-menu offset-y>
                            <template v-slot:activator="{ on, attrs }">
                                <v-btn
                                    class="white--text rounded-pill px-5 py-2 mx-1"
                                    color="yellowish"
                                    width="auto"
                                    min-height="32px"
                                    style="letter-spacing:0px;" 
                                    elevation="0"
                                    v-bind="attrs"
                                    v-on="on"
                                >
                                    More
                                </v-btn>
                            </template>
                            <v-list>
                                <v-list-item
                                    v-for="restCat in restCategory"
                                    :key="restCat.id"
                                >
                                    <v-list-item-title 
                                        @click="changeContent(restCat.id)"
                                        style="cursor: pointer"
                                    >
                                        {{ restCat.cat }}
                                    </v-list-item-title>
                                </v-list-item>
                            </v-list>
                        </v-menu>
                    </v-btn-toggle>
                </div>
                <div class="content">
                    <v-row class="mx-0">
                        <v-col
                            md="4"
                            sm="6"
                            xs="12" 
                            v-for="event in eventList"
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
                                            color="white"
                                            width="auto"
                                            min-height="32px"
                                            style="letter-spacing:0px; cursor: default;" 
                                            elevation="0"
                                        >
                                            {{event.status}}
                                        </v-btn>
                                        <v-btn
                                            class="white--text px-4 rounded-pill"
                                            width="auto"
                                            min-height="32px"
                                            color="yellowish"
                                            style="letter-spacing:0px; cursor: default;" 
                                            elevation="0" 
                                        >
                                            <span v-show="!(event.cost == 'Free')">$</span> 
                                            {{event.cost}}
                                        </v-btn>
                                    </div>
                                </v-img>
                                <v-card-title
                                    class="pl-0"
                                    @click="getEvent(event.id)"
                                >
                                    <NuxtLink :to="{path: 'Events/Detail/'+(event.title).split(' ').join('-')}">
                                        {{event.title}}
                                    </NuxtLink>
                                </v-card-title>
                                <div
                                    class="d-flex flex-wrap pl-0"
                                >
                                    <NuxtLink :to="{path: 'Events/Category/'+(event.category).charAt(0).toUpperCase()+(event.category).slice(1) }">
                                        <v-btn
                                            class="white--text px-4 rounded-pill"
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
                                        >
                                            mdi-calendar-outline
                                        </v-icon>
                                        <span class="text--secondary ml-2">{{event.date}}</span>
                                    </span>

                                    <span class="d-flex align-center py-2">
                                        <v-icon
                                            color="yellowish"
                                        >
                                            mdi-map-marker-outline
                                        </v-icon>
                                        <span class="text--secondary ml-2">
                                            <NuxtLink :to="{path: 'Venues/Location/'+(event.location).charAt(0).toUpperCase()+(event.location).slice(1) }">
                                                {{event.location}}
                                            </NuxtLink>
                                        </span>
                                    </span>

                                </div>
                                <v-card-text
                                    class="pl-0"
                                >
                                    {{event.description}}
                                </v-card-text>
                            </v-card>
                        </v-col>
                    </v-row>
                </div>
                <div
                    class="d-flex justify-center my-9"
                >
                    <NuxtLink to="Events">
                        <v-btn 
                            class="btn-style mx-5 px-6 grey--text rounded-lg"
                            height="50px"
                            elevation="0"
                        >
                            All Events
                        </v-btn>
                    </NuxtLink>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
    export default {
        name: 'UpcomingEvent', 
        data:() => ({
            w: '', 
            categories: [
                {
                    id: 1, 
                    cat: 'Art', 
                },
                {
                    id: 2, 
                    cat: 'Business', 
                },
                {
                    id: 3, 
                    cat: 'Concert', 
                },
                {
                    id: 4, 
                    cat: 'Conferrence', 
                },
                {
                    id: 5, 
                    cat: 'Education', 
                },
                {
                    id: 6, 
                    cat: 'Festival', 
                },
                {
                    id: 7, 
                    cat: 'Food', 
                },
                {
                    id: 8, 
                    cat: 'Micellaneous', 
                },
                {
                    id: 9, 
                    cat: 'Nightlife', 
                },
                {
                    id: 10, 
                    cat: 'Sports', 
                },
                {
                    id: 11, 
                    cat: 'Technology', 
                },
                {
                    id: 12, 
                    cat: 'Travel', 
                },
                {
                    id: 13, 
                    cat: 'Wedding', 
                },
            ], 
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
            eventList: [], 
            toggle_one: 0, 
            categoryCount: 7, 
            listCategory:[], 
            restCategory: [], 
            tabs: null, 
            text: 'rxdctfvgbh zsxrdcfvgbhnjm xrdctfvgbhnj xrdctvygbhn zsxrdctvgbuhni'

        }), 
        methods:{
            async getEvent(id){
                localStorage.setItem("eventId", id); 
            }, 
            
            async changeContent(i){
                if(i== 0){
                    if(this.events.length > 6){
                        this.eventList = this.events.slice(0,6); 
                    }
                    else{
                       this.eventList = this.events;  
                    }
                }
                else{
                    this.eventList = this.events.filter((x) => x.catId === i);
                    if(this.eventList.length > 6){
                        this.eventList = this.eventList.slice(0,6); 
                    }
                }
            },
            async getWindowSize(){
                this.w = window.innerWidth;
            },
        },
        mounted(){
            const lengthCat = this.categories.length; 
            // console.log(lengthCat); 
            this.changeContent(0); 
            this.getWindowSize(); 

            if(this.w > 1264){
                this.categoryCount= 7; 
                if(this.categories.length > this.categoryCount){ 
                    this.listCategory = this.categories.slice(0, this.categoryCount); 
                    this.restCategory =  this.categories.slice((this.categories.length - this.categoryCount) * -1);
                    // console.log(this.listCategory); 
                    // console.log(this.restCategory); 
                }
                else{
                    this.listCategory = this.categories; 
                }
            }
            else if(this.w < 1264 && this.w >= 960){
                this.categoryCount= 5; 
                if(this.categories.length > this.categoryCount){ 
                    this.listCategory = this.categories.slice(0, this.categoryCount); 
                    this.restCategory =  this.categories.slice((this.categories.length - this.categoryCount) * -1);
                    // console.log(this.listCategory); 
                    // console.log(this.restCategory); 
                }
                else{
                    this.listCategory = this.categories; 
                }
            }
            else if(this.w < 960 && this.w >600){
                this.categoryCount= 3; 
                if(this.categories.length > this.categoryCount){ 
                    this.listCategory = this.categories.slice(0, this.categoryCount); 
                    this.restCategory =  this.categories.slice((this.categories.length - this.categoryCount) * -1);
                }
                else{
                    this.listCategory = this.categories; 
                }
            }
            else if(this.w < 600){
                this.categoryCount= 2; 
                if(this.categories.length > this.categoryCount){ 
                    this.listCategory = this.categories.slice(0, this.categoryCount); 
                    this.restCategory =  this.categories.slice((this.categories.length - this.categoryCount) * -1);
                }
                else{
                    this.listCategory = this.categories; 
                }
            }
        },
    }
</script>

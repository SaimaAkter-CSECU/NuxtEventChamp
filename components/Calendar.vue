<template>
    <div class="subPageContent">
        <div class="container--fluid">
            <div class="content-div">
                <div class="search-div my-5">
                    <v-row>
                        <v-col
                            cols="12"
                            sm="9"
                            xs="12"
                            class="pr-0"
                        >
                            <v-text-field
                                v-model="keyword"
                                
                                placeholder="Search Event Dates or Event Names...."
                                block
                                outlined
                            ></v-text-field>
                        </v-col>
                        <v-col
                            col="12"
                            sm="3"
                            xs="12"
                        >
                            <v-btn 
                                class="btn-yellowish-style"
                                style="letter-spacing:0px;"  
                                block
                                x-large
                                elevation="0"
                            >
                                search
                            </v-btn>
                        </v-col>
                    </v-row>
                </div>
                <div
                    v-for="date in dates"
                    :key="date.id"
                >
                    <div
                        width="100%"
                        class="mb-5"
                    >
                        <div
                            class="black white--text d-flex justify-space-between align-center px-8"
                            style="min-height: 4.5rem;" 
                        >
                            <div
                                class="subtitle-1 font-weight-medium"
                            >
                                {{date.date}}
                            </div>
                            <div
                                class="subtitle-1 font-weight-medium"
                            >
                                {{date.day}}
                            </div>
                        </div>
                        <div class="white black--text text--secondary px-8">
                            <div
                                v-for="event in date.events"
                                :key="event.id"
                            >
                                <v-row>
                                    <v-col
                                        cols="12"
                                        md="2"
                                        sm="3"
                                        xs="4" 
                                    >
                                        <div
                                            class="text-p grey--text text--primary"
                                        >
                                            {{event.duration}}
                                        </div>
                                    </v-col>
                                    <v-col
                                        cols="12"
                                        md="10"
                                        sm="9"
                                        xs="8" 
                                    >
                                        <div
                                            class="text-p grey--text text--primary eventLink"
                                        >
                                            <NuxtLink :to="{path: '../Events/Detail/'+(event.title).split(' ').join('-')}">
                                                {{event.title}}
                                            </NuxtLink>
                                        </div>
                                    </v-col>
                                </v-row>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'Calendar',
        data: () => ({
            dates:[
                {
                    id: 1,
                    date: 'October 1, 2021',
                    day: 'Friday',
                    events: [
                        {
                            id: 1,
                            title: 'Eventchamp Conference',
                            duration: 'All Day'
                        },
                        {
                            id: 2,
                            title: 'Fashion Carnival 2021',
                            duration: 'All Day'
                        },
                        {
                            id: 3,
                            title: 'Gaming X2021 Fair',
                            duration: 'All Day'
                        },
                        {
                            id: 4,
                            title: 'Milano 21T Meeting',
                            duration: 'All Day'
                        },
                        {
                            id: 5,
                            title: 'The Future of Currencies',
                            duration: 'All Day'
                        },
                        {
                            id: 6,
                            title: 'Wedding of James & Helen',
                            duration: 'All Day'
                        },	
                    ]
                },
                {
                    id: 2,
                    date: 'October 2, 2021',
                    day: 'Saturday',
                    events: [
                        {
                            id: 1,
                            title: 'Eventchamp Conference',
                            duration: 'All Day'
                        },
                        {
                            id: 2,
                            title: 'Fashion Carnival 2021',
                            duration: 'All Day'
                        },
                        {
                            id: 3,
                            title: 'Gaming X2021 Fair',
                            duration: 'All Day'
                        },
                        {
                            id: 4,
                            title: 'Milano 21T Meeting',
                            duration: 'All Day'
                        },
                        {
                            id: 5,
                            title: 'The Future of Currencies',
                            duration: 'All Day'
                        },
                        {
                            id: 6,
                            title: 'Wedding of James & Helen',
                            duration: 'All Day'
                        },	
                        {
                            id: 7,
                            title: 'Drama Games 2021',
                            duration: 'All Day'
                        },
                    ]
                },
                {
                    id: 3,
                    date: 'October 3, 2021',
                    day: 'Sunday',
                    events: [
                        {
                            id: 1,
                            title: 'Eventchamp Conference',
                            duration: 'All Day'
                        },
                        {
                            id: 2,
                            title: 'Fashion Carnival 2021',
                            duration: 'All Day'
                        },
                        {
                            id: 3,
                            title: 'Gaming X2021 Fair',
                            duration: 'All Day'
                        },
                        {
                            id: 4,
                            title: 'Milano 21T Meeting',
                            duration: 'All Day'
                        },
                        {
                            id: 5,
                            title: 'The Future of Currencies',
                            duration: 'All Day'
                        },
                        {
                            id: 6,
                            title: 'Wedding of James & Helen',
                            duration: 'All Day'
                        },	
                    ]
                },
                {
                    id: 4,
                    date: 'October 4, 2021',
                    day: 'Monday',
                    events: [
                        {
                            id: 1,
                            title: 'Eventchamp Conference',
                            duration: 'All Day'
                        },
                        {
                            id: 2,
                            title: 'Fashion Carnival 2021',
                            duration: 'All Day'
                        },
                        {
                            id: 3,
                            title: 'Gaming X2021 Fair',
                            duration: 'All Day'
                        },
                        {
                            id: 4,
                            title: 'Milano 21T Meeting',
                            duration: 'All Day'
                        },
                        {
                            id: 5,
                            title: 'The Future of Currencies',
                            duration: 'All Day'
                        },
                        {
                            id: 6,
                            title: 'Wedding of James & Helen',
                            duration: 'All Day'
                        },	
                        {
                            id: 7,
                            title: 'Drama Games 2021',
                            duration: 'All Day'
                        },
                    ]
                },
                {
                    id: 5,
                    date: 'October 5, 2021',
                    day: 'Tuesday',
                    events: [
                        {
                            id: 1,
                            title: 'Eventchamp Conference',
                            duration: 'All Day'
                        },
                        {
                            id: 2,
                            title: 'Fashion Carnival 2021',
                            duration: 'All Day'
                        },
                        {
                            id: 3,
                            title: 'Gaming X2021 Fair',
                            duration: 'All Day'
                        },
                        {
                            id: 4,
                            title: 'Milano 21T Meeting',
                            duration: 'All Day'
                        },
                        {
                            id: 5,
                            title: 'The Future of Currencies',
                            duration: 'All Day'
                        },
                        {
                            id: 6,
                            title: 'Wedding of James & Helen',
                            duration: 'All Day'
                        },	
                    ]
                },
                {
                    id: 6,
                    date: 'October 6, 2021',
                    day: 'Wednesday',
                    events: [
                        {
                            id: 1,
                            title: 'Eventchamp Conference',
                            duration: 'All Day'
                        },
                        {
                            id: 2,
                            title: 'Fashion Carnival 2021',
                            duration: 'All Day'
                        },
                        {
                            id: 3,
                            title: 'Gaming X2021 Fair',
                            duration: 'All Day'
                        },
                        {
                            id: 4,
                            title: 'Milano 21T Meeting',
                            duration: 'All Day'
                        },
                        {
                            id: 5,
                            title: 'The Future of Currencies',
                            duration: 'All Day'
                        },
                        {
                            id: 6,
                            title: 'Wedding of James & Helen',
                            duration: 'All Day'
                        },	
                        {
                            id: 7,
                            title: 'Drama Games 2021',
                            duration: 'All Day'
                        },
                    ]
                },
                {
                    id: 7,
                    date: 'October 7, 2021',
                    day: 'Thursday',
                    events: [
                        {
                            id: 1,
                            title: 'Eventchamp Conference',
                            duration: 'All Day'
                        },
                        {
                            id: 2,
                            title: 'Fashion Carnival 2021',
                            duration: 'All Day'
                        },
                        {
                            id: 3,
                            title: 'Gaming X2021 Fair',
                            duration: 'All Day'
                        },
                        {
                            id: 4,
                            title: 'Milano 21T Meeting',
                            duration: 'All Day'
                        },
                        {
                            id: 5,
                            title: 'The Future of Currencies',
                            duration: 'All Day'
                        },
                        {
                            id: 6,
                            title: 'Wedding of James & Helen',
                            duration: 'All Day'
                        },	
                    ]
                },
                {
                    id: 8,
                    date: 'October 8, 2021',
                    day: 'Friday',
                    events: [
                        {
                            id: 1,
                            title: 'Eventchamp Conference',
                            duration: 'All Day'
                        },
                        {
                            id: 2,
                            title: 'Fashion Carnival 2021',
                            duration: 'All Day'
                        },
                        {
                            id: 3,
                            title: 'Gaming X2021 Fair',
                            duration: 'All Day'
                        },
                        {
                            id: 4,
                            title: 'Milano 21T Meeting',
                            duration: 'All Day'
                        },
                        {
                            id: 5,
                            title: 'The Future of Currencies',
                            duration: 'All Day'
                        },
                        {
                            id: 6,
                            title: 'Wedding of James & Helen',
                            duration: 'All Day'
                        },	
                        {
                            id: 7,
                            title: 'Drama Games 2021',
                            duration: 'All Day'
                        },
                    ]
                },
                {
                    id: 9,
                    date: 'October 9, 2021',
                    day: 'Saturday',
                    events: [
                        {
                            id: 1,
                            title: 'Eventchamp Conference',
                            duration: 'All Day'
                        },
                        {
                            id: 2,
                            title: 'Fashion Carnival 2021',
                            duration: 'All Day'
                        },
                        {
                            id: 3,
                            title: 'Gaming X2021 Fair',
                            duration: 'All Day'
                        },
                        {
                            id: 4,
                            title: 'Milano 21T Meeting',
                            duration: 'All Day'
                        },
                        {
                            id: 5,
                            title: 'The Future of Currencies',
                            duration: 'All Day'
                        },
                        {
                            id: 6,
                            title: 'Wedding of James & Helen',
                            duration: 'All Day'
                        },	
                    ]
                },
                {
                    id: 10,
                    date: 'October 10, 2021',
                    day: 'Sunday',
                    events: [
                        {
                            id: 1,
                            title: 'Eventchamp Conference',
                            duration: 'All Day'
                        },
                        {
                            id: 2,
                            title: 'Fashion Carnival 2021',
                            duration: 'All Day'
                        },
                        {
                            id: 3,
                            title: 'Gaming X2021 Fair',
                            duration: 'All Day'
                        },
                        {
                            id: 4,
                            title: 'Milano 21T Meeting',
                            duration: 'All Day'
                        },
                        {
                            id: 5,
                            title: 'The Future of Currencies',
                            duration: 'All Day'
                        },
                        {
                            id: 6,
                            title: 'Wedding of James & Helen',
                            duration: 'All Day'
                        },	
                        {
                            id: 7,
                            title: 'Drama Games 2021',
                            duration: 'All Day'
                        },
                    ]
                },
            ],
            keyword: '', 
        }),
    }
</script>

<template>
    <div
        class="white advertise-div rounded-lg"
    >
        <div
            class="py-7 px-9 text-h6 d-flex justify-space-between align-center flex-wrap"
            style="border-bottom: 1px solid #eaeaea"
        >
            <span>Event Details</span>
            <span>
                <span>
                    <v-btn
                        style="border: 1px solid #eaeaea;"
                        class="rounded-md" 
                        elevation="0"
                    >
                        <v-icon>
                            mdi-heart-outline
                        </v-icon>
                        <span class="ml-1">{{whishCount}}</span>
                    </v-btn>
                </span>
                <span>
                    <v-btn
                        style="border: 1px solid #eaeaea;"
                        class="rounded-md" 
                        elevation="0"
                    >
                        <v-icon>
                            mdi-star-outline
                        </v-icon>
                    </v-btn>
                </span>
            </span>
        </div>
        <div
            class="pa-8 pt-3"
        >
            <div
                class="py-5"
                v-for="detail in eventDetails"
                :key="detail.id"
            >
                <v-row
                    class="align-center"
                    style="border-bottom: 1px solid #eaeaea"
                >
                    <v-col
                        col="12"
                        md="2"
                        sm="3"
                        xs="3"
                    >
                        <v-icon
                            color="yellowish"
                            large
                            class="font-weight-thin"
                        >
                            {{detail.icon}}
                        </v-icon>
                    </v-col>
                    <v-col
                        col="12"
                        md="10"
                        sm="9"
                        xs="9"
                    >
                        <div
                            class="subtitle-2 font-weight-medium mb-1 text-uppercase"
                        >
                            {{detail.title}}
                        </div>
                        <div
                            class="text-p grey--text font-weight-normal mb-1"
                        >
                            {{detail.value}}
                        </div>
                    </v-col>
                </v-row>
            </div>
            <v-row
                class="align-center pt-5"
            >
                <v-col
                    col="12"
                    md="2"
                    sm="3"
                    xs="3"
                >
                    <v-icon
                        color="yellowish"
                        large
                        class="font-weight-thin"
                    >
                        mdi-share-variant-outline
                    </v-icon>
                </v-col>
                <v-col
                    col="12"
                    md="10"
                    sm="9"
                    xs="9"
                >
                    <div
                        class="subtitle-2 font-weight-medium mb-1 text-uppercase"
                    >
                        Network
                    </div>
                    <div
                        class="text-p grey--text font-weight-normal mb-1 d-flex align-center flex-wrap"
                    >
                        <a 
                            :href="eventFacebook"
                            class="mr-1" 
                        >
                            <v-icon
                                color="grey darken-1"
                            >
                                mdi-alpha-f
                            </v-icon>
                        </a>
                        <a 
                            :href="eventInstagram"
                            class="mr-2"
                        >
                            <v-icon
                                color="grey darken-1"
                                small
                            >
                                mdi-instagram
                            </v-icon>
                        </a>
                        <a 
                            :href="eventTwitter"
                            class="mr-2"
                        >
                            <v-icon
                                color="grey darken-1"
                                small
                            >
                                mdi-twitter
                            </v-icon>
                        </a>
                        <a 
                            :href="eventYoutube"
                            class="mr-2"
                        >
                            <v-icon
                                color="grey darken-1"
                                small
                            >
                                mdi-youtube
                            </v-icon>
                        </a>
                    </div>
                </v-col>
            </v-row>
        </div>
        
    </div>
</template>

<script>
    
    export default {
        name: 'SidebarEventDetails',
        props: ['event'], 
        data: () => ({
            eventFacebook: '',
            eventInstagram: '', 
            eventYoutube: '', 
            eventTwitter: '', 
            whishCount: '', 
            eventDetails: [],
            
        }),
        mounted() {
            // console.log(this.event); 
            this.eventDetails= [
                {
                    id: 1,
                    title: 'Start Date',
                    value: this.event[0].startDate,
                    icon: 'mdi-calendar-clock-outline', 
                },
                {
                    id: 2,
                    title: 'End Date',
                    value: this.event[0].endDate,
                    icon: 'mdi-calendar-clock-outline', 
                },
                {
                    id: 3,
                    title: 'Status',
                    value: this.event[0].status,
                    icon: 'mdi-check-circle-outline', 
                },
                {
                    id: 4,
                    title: 'Location',
                    value: this.event[0].location,
                    icon: 'mdi-map-marker-outline', 
                },
                {
                    id: 5,
                    title: 'Venue',
                    value: this.event[0].venue,
                    icon: 'mdi-map-marker-radius-outline', 
                },
                {
                    id: 6,
                    title: 'organizer',
                    value: this.event[0].organizer,
                    icon: 'mdi-account-outline', 
                },
                {
                    id: 7,
                    title: 'category',
                    value: this.event[0].category,
                    icon: 'mdi-folder-open-outline', 
                },
                {
                    id: 8,
                    title: 'address',
                    value: this.event[0].address,
                    icon: 'mdi-flag-outline', 
                },
                {
                    id: 9,
                    title: 'phone',
                    value: this.event[0].phone,
                    icon: 'mdi-phone-in-talk-outline', 
                },
                {
                    id: 10,
                    title: 'email',
                    value: this.event[0].email,
                    icon: 'mdi-email-outline', 
                },
                {
                    id: 11,
                    title: 'Remaining Tickets',
                    value: this.event[0].remainingTickets,
                    icon: 'mdi-ticket-percent-outline', 
                },
            ]
            
        },
    }
</script>
<template>
    <div>
        <div
            class="white venue-detail-div rounded-lg"
        >
            <div
                class="py-7 px-9 text-h6 d-flex justify-space-between align-center flex-wrap"
                style="border-bottom: 1px solid #eaeaea"
            >
                <span>Venue Details</span>
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
                    v-for="detail in venueDetails"
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
                                :href="venueFacebook"
                                class="mr-1" 
                            >
                                <v-icon
                                    color="grey darken-1"
                                >
                                    mdi-alpha-f
                                </v-icon>
                            </a>
                            <a 
                                :href="venueInstagram"
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
                                :href="venueTwitter"
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
                                :href="venueYoutube"
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

        <div
            class="white venue-detail-div rounded-lg mt-9"
        >
            <div
                class="py-7 px-9 text-h6"
                style="border-bottom: 1px solid #eaeaea"
            >
                Working Hours
            </div>

            <div
                class="pa-8 pt-3"
            >
                <div
                    class="py-5"
                    v-for="workingHour in venueDetailsWorkingHours"
                    :key="workingHour.id"
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
                                {{workingHour.icon}}
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
                                {{workingHour.title}}
                            </div>
                            <div
                                class="text-p grey--text font-weight-normal mb-1"
                            >
                                {{workingHour.value}}
                            </div>
                        </v-col>
                    </v-row>
                </div>
            </div>
        </div>

        <!-- <div
            class="white venue-detail-div rounded-lg mt-9"
        >
            <div
                class="py-7 px-9 text-h6"
                style="border-bottom: 1px solid #eaeaea"
            >
                Venue Map
            </div>

            <div
                class="pa-8 pt-3"
            >
                <div
                    class="py-5"
                    v-for="venueDetailsWorkingHour in venueDetailsWorkingHours"
                    :key="venueDetailsWorkingHour.id"
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
                                {{venueDetailsWorkingHour.icon}}
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
                                {{venueDetailsWorkingHour.title}}
                            </div>
                            <div
                                class="text-p grey--text font-weight-normal mb-1"
                            >
                                {{venueDetailsWorkingHour.value}}
                            </div>
                        </v-col>
                    </v-row>
                </div>
            </div>
        </div> -->
    </div>
</template>

<script>
    
    export default {
        name: 'SidebarVenueDetails',
        props: ['venue'], 
        data: () => ({
            
            venueFacebook: '',
            venueInstagram: '', 
            venueYoutube: '', 
            venueTwitter: '', 
            whishCount: '', 
            venueDetails: [],
            venueDetailsWorkingHours: [],
            
        }),
        mounted() {
            console.log('venue ', this.venue); 
            this.venueDetails= [
                {
                    id: 1,
                    title: 'Location',
                    value: this.venue.location,
                    icon: 'mdi-map-marker-outline', 
                },
                {
                    id: 2,
                    title: 'Category',
                    value: this.venue.category,
                    icon: 'mdi-folder-open-outline', 
                },
                {
                    id: 3,
                    title: 'Address',
                    value: this.venue.address,
                    icon: 'mdi-flag-outline', 
                },
                {
                    id: 4,
                    title: 'phone',
                    value: this.venue.phone,
                    icon: 'mdi-phone-in-talk-outline', 
                },
                {
                    id: 5,
                    title: 'email',
                    value: this.venue.email,
                    icon: 'mdi-email-outline', 
                },
                {
                    id: 6,
                    title: 'website',
                    value: this.venue.website,
                    icon: 'mdi-web-sync', 
                },
                
            ];
            this.venueDetailsWorkingHours = [
                {
                    id: 1,
                    title: 'weekdays',
                    value: this.venue.weekdays,
                    icon: 'mdi-calendar-month-outline', 
                },
                {
                    id: 2,
                    title: 'saturday',
                    value: this.venue.saturday,
                    icon: 'mdi-calendar-month-outline', 
                },
                {
                    id: 3,
                    title: 'sunday',
                    value: this.venue.sunday,
                    icon: 'mdi-calendar-month-outline', 
                },
            ];
            this.venueFacebook = this.venue.venueFacebook;
            this.venueInstagram = this.venue.venueInstagram;
            this.venueYoutube = this.venue.venueYoutube;
            this.venueTwitter = this.venue.venueTwitter;
            this.whishCount = this.venue.whishCount; 

            console.log('venueDetails ',this.venueDetails); 
            console.log('venueDetailsWorkingHours ', this.venueDetailsWorkingHours);
            
        },
    }
</script>
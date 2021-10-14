<template>
    <div
        class="white advertise-div rounded-lg mt-9"
    >
        <div
            class="py-7 px-9 text-h6"
            style="border-bottom: 1px solid #eaeaea"
        >
            Sponsors
        </div>
        <div
            class="pa-8 pt-3"
        >
            <v-row>
                <v-col
                    col="12"
                    sm="6"
                    xs="12"
                    v-for="sponsor in sponsorList"
                    :key="sponsor.id"
                >
                    <div
                        class="rounded-lg"
                        style="border: 1px solid #eaeaea"
                    >
                        <a :href="sponsor.link">
                            <v-img
                                :src="sponsor.img"
                                class="rounded-lg"
                                width="100%"
                                height="100%"
                            ></v-img>
                        </a> 
                    </div>
                </v-col>
            </v-row>
            <!-- <div
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
            </div> -->
        </div>
        
    </div>
</template>

<script>
    
    export default {
        name: 'SidebarVenueSponsor',
        props: ['venue'], 
        data: () => ({
            sponsorList: [],
            
        }),
        mounted() {
            console.log(this.venue.sponsors); 
            this.sponsorList = this.venue.sponsors; 
            console.log(this.sponsorList)
        },
    }
</script>
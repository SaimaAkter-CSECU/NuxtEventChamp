<template>
    <div
        class="white speaker-details-div rounded-lg"
    >
        <div
            class="py-7 px-9 text-h6 d-flex justify-space-between align-center flex-wrap"
            style="border-bottom: 1px solid #eaeaea"
        >
            <span>Speaker Details</span>
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
                v-for="detail in speakerDetails"
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
                            :href="facebookLink"
                            class="mr-1" 
                        >
                            <v-icon
                                small
                                color="grey darken-1"
                            >
                                mdi-facebook
                            </v-icon>
                        </a>
                        <a 
                            :href="instagramLink"
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
                            :href="twitterLink"
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
                            :href="websiteLink"
                            class="mr-2"
                        >
                            <v-icon
                                color="grey darken-1"
                                small
                            >
                                mdi-web-sync
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
    name: 'SidebarSpeakerDetails', 
    props: ['speaker'],
    data: () => ({
        speakerDetails: [], 
        facebookLink: '',
        instagramLink: '',
        twitterLink: '',
        websiteLink: '', 
        whishCount: 7, 
    }),
    mounted() {
        console.log(this.speaker)
        this.speakerDetails= [
            {
                id: 1,
                title: 'Category',
                value: this.speaker.designation,
                icon: 'mdi-folder-open-outline', 
            },
            {
                id: 2,
                title: 'Location',
                value: this.speaker.location,
                icon: 'mdi-map-marker-outline', 
            },
            {
                id: 3,
                title: 'Address',
                value: this.speaker.address,
                icon: 'mdi-flag-outline', 
            },
            {
                id: 4,
                title: 'phone',
                value: this.speaker.phone,
                icon: 'mdi-phone-in-talk-outline', 
            },
            {
                id: 5,
                title: 'email',
                value: this.speaker.email,
                icon: 'mdi-email-outline', 
            },
            {
                id: 6,
                title: 'website',
                value: this.speaker.website,
                icon: 'mdi-web-sync', 
            },
        ];
        this.facebookLink = this.speaker.facebookLink;
        this.instagramLink = this.speaker.instagramLink;
        this.twitterLink = this.speaker.twitterLink;
        this.websiteLink = this.speaker.websiteLink;
        this.whishCount = this.speaker.whishCount;
    },
}
</script>
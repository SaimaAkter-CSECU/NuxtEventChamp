<template>
    <section>
        <div class="section-title text-center">
            <div class="text-h3">
                Related <span class="yellowish--text font-weight-medium">Speakers</span>
            </div>
            <div class="section-divider d-flex align-center justify-center my-9"> 
                <v-divider
                    style="max-width: 150px !important; width: 150px !important"
                ></v-divider>
                <v-icon
                    class="mx-2"
                    
                    color="grey lighten-2"
                >
                    mdi-headphones
                </v-icon>
                <v-divider
                    style="max-width: 150px !important; width: 150px !important"
                ></v-divider>
            </div>
            <div class="text-center mb-9">
                <div class="text-p font-weight-normal grey--text lighten-1">
                    You might also love these speakers.
                </div>
            </div>
        </div>
        <div class="section-content">
            <div class="content-div">
                <v-row
                    class="relatedSpeakers"
                >
                    <v-col
                        col="12"
                        md="4"
                        sm="6"
                        xs="12"
                        v-for="speaker in speakers"
                        :key="speaker.id"
                    >
                        <v-img
                            :src="speaker.url"
                            class="rounded-md"
                        >
                            <div 
                                class="overlay pa-9 rounded-md"
                            >
                                <v-card
                                    color="transparent"
                                    elevation="0"
                                    class="rounded-md"
                                >
                                    <v-card-title
                                        class="mb-3 px-4 white--text"
                                        @click="getSpeaker(speaker.id)"
                                    >
                                        <NuxtLink :to="{path: './'+(speaker.name).split(' ').join('-') }">
                                            {{speaker.name}}
                                        </NuxtLink>
                                    </v-card-title>
                                    <v-card-subtitle
                                        class="subtitle-2 font-weight-bold white--text text-uppercase px-4"
                                        color="white"
                                    >
                                        {{speaker.designation}}
                                    </v-card-subtitle>
                                    <v-card-text
                                        class="white--text px-4 visibleText mt-5 mb-3"
                                    >
                                        {{speaker.description}}
                                    </v-card-text>
                                    <v-card-actions
                                        class="px-4 visibleText"
                                    >
                                        <a :href="speaker.facebookLink" target="_blank">
                                            <v-icon
                                                color="white"
                                                class="mr-2"
                                            >
                                                mdi-facebook
                                            </v-icon>
                                        </a>
                                        <a :href="speaker.instagramLink" target="_blank">
                                            <v-icon
                                                color="white"
                                                class="mr-2"
                                            >
                                                mdi-instagram
                                            </v-icon>
                                        </a>
                                        <a :href="speaker.twitterLink" target="_blank">
                                            <v-icon
                                                color="white"
                                                class="mr-2"
                                            >
                                                mdi-twitter
                                            </v-icon>
                                        </a>
                                        <a :href="speaker.websiteLink" target="_blank">
                                            <v-icon
                                                color="white"
                                                class="mr-2"
                                            >
                                                mdi-web-sync
                                            </v-icon>
                                        </a>
                                    </v-card-actions>
                                </v-card>
                            </div>
                        </v-img>
                    </v-col>
                </v-row>
            </div>
        </div>
    </section>
</template>

<script>
    export default {
        name: 'RelatedSpeakers', 
        data: () => ({
            speakers: [
                {
                    id: 1, 
                    name: 'Roberto Berry',
                    designation: 'CEO & FOUNDER',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad ne nec dolore oblique nusquam.',
                    facebookLink: 'https://www.facebook.com/',
                    instagramLink: 'https://www.instagram.com/',
                    twitterLink: 'https://twitter.com/',
                    websiteLink: 'https://www.facebook.com', 
                    url: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/speaker-13-350x350.jpg',
                },
                {
                    id: 2, 
                    name: 'Saul R. Lopez',
                    designation: 'CEO & FOUNDER',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad ne nec dolore oblique nusquam.',
                    facebookLink: 'https://www.facebook.com/',
                    instagramLink: 'https://www.instagram.com/',
                    twitterLink: 'https://twitter.com/',
                    websiteLink: 'https://www.facebook.com', 
                    url: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/speaker-12-350x350.jpg',
                },
                {
                    id: 3, 
                    name: 'Thomas Childers',
                    designation: 'manager',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad ne nec dolore oblique nusquam.',
                    facebookLink: 'https://www.facebook.com/',
                    instagramLink: 'https://www.instagram.com/',
                    twitterLink: 'https://twitter.com/',
                    websiteLink: 'https://www.facebook.com', 
                    url: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/speaker-11-350x350.jpg',
                },
            ]
        }),
        methods: {
            async getSpeaker(id){
                localStorage.setItem("speakerId", id)
            }
        },
    }
</script>
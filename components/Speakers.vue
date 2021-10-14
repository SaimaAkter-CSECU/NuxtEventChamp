<template>
    <div class="subPageContent">
        <div class="container--fluid">
            <div class="content-div">
                <v-row>
                    <v-col
                        col="12"
                        md="6"
                        sm="6"
                        xs="12"
                        v-for="speaker in speakers"
                        :key="speaker.id"
                    >
                        <v-card
                            class="mb-9 pa-4"
                            elevation="0"
                        >
                            <v-row
                                class="align-center"
                            >
                                <v-col
                                    col="12"
                                    md="5"
                                    sm="5"
                                    xs="12"
                                    class="pa-0 photos-div"
                                >
                                    <NuxtLink :to="{path: 'Speakers/Detail/'+(speaker.name).split(' ').join('-') }">
                                        <v-img
                                            :src="speaker.url"
                                            @click="getSpeaker(speaker.id)"
                                        >
                                            <div class="overlay"></div>
                                        </v-img>
                                    </NuxtLink>
                                </v-col>
                                <v-col
                                    col="12"
                                    md="7"
                                    sm="7"
                                    xs="12"
                                    class="pa-0"
                                >
                                    <v-card-title
                                        class="mb-3 px-4"
                                        @click="getSpeaker(speaker.id)"
                                    >
                                        <NuxtLink :to="{path: 'Speakers/Detail/'+(speaker.name).split(' ').join('-') }">
                                            {{speaker.name}}
                                        </NuxtLink>
                                    </v-card-title>
                                    <v-card-subtitle
                                        class="subtitle-2 font-weight-bold grey--text text-uppercase px-4 text--secondary"
                                    >
                                        {{speaker.designation}}
                                    </v-card-subtitle>
                                    <v-card-text
                                        class="text--secondary grey--text  px-4"
                                    >
                                        {{speaker.description}}
                                    </v-card-text>
                                    <v-card-actions
                                        class="px-4"
                                    >
                                        <a :href="speaker.facebookLink" target="_blank">
                                            <v-icon
                                                small
                                                color="grey darken-1"
                                                class="mr-2"
                                            >
                                                mdi-facebook
                                            </v-icon>
                                        </a>
                                        <a :href="speaker.instagramLink" target="_blank">
                                            <v-icon
                                                small
                                                color="grey darken-1"
                                                class="mr-2"
                                            >
                                                mdi-instagram
                                            </v-icon>
                                        </a>
                                        <a :href="speaker.twitterLink" target="_blank">
                                            <v-icon
                                                small
                                                color="grey darken-1"
                                                class="mr-2"
                                            >
                                                mdi-twitter
                                            </v-icon>
                                        </a>
                                        <a :href="speaker.websiteLink" target="_blank">
                                            <v-icon
                                                small
                                                color="grey darken-1"
                                                class="mr-2"
                                            >
                                                mdi-web-sync
                                            </v-icon>
                                        </a>
                                    </v-card-actions>
                                </v-col>
                            </v-row>
                        </v-card>
                    </v-col>
                </v-row>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        name: "Speakers",
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
                {
                    id: 4, 
                    name: 'Frances B. Chandler',
                    designation: 'analyst',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad ne nec dolore oblique nusquam.',
                    facebookLink: 'https://www.facebook.com/',
                    instagramLink: 'https://www.instagram.com/',
                    twitterLink: 'https://twitter.com/',
                    websiteLink: 'https://www.facebook.com', 
                    url: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/speaker-10-350x350.jpg',
                },
                {
                    id: 5, 
                    name: 'Melek Ozcan',
                    designation: 'CEO & FOUNDER',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad ne nec dolore oblique nusquam.',
                    facebookLink: 'https://www.facebook.com/',
                    instagramLink: 'https://www.instagram.com/',
                    twitterLink: 'https://twitter.com/',
                    websiteLink: 'https://www.facebook.com', 
                    url: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/speaker-9-350x350.jpg',
                },
                {
                    id: 6, 
                    name: 'Mary Griffin',
                    designation: 'designer',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad ne nec dolore oblique nusquam.',
                    facebookLink: 'https://www.facebook.com/',
                    instagramLink: 'https://www.instagram.com/',
                    twitterLink: 'https://twitter.com/',
                    websiteLink: 'https://www.facebook.com', 
                    url: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/speaker-13-350x350.jpg',
                },
                {
                    id: 7, 
                    name: 'Babette Chauvet',
                    designation: 'designer',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad ne nec dolore oblique nusquam.',
                    facebookLink: 'https://www.facebook.com/',
                    instagramLink: 'https://www.instagram.com/',
                    twitterLink: 'https://twitter.com/',
                    websiteLink: 'https://www.facebook.com', 
                    url: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/speaker-7-350x350.jpg',
                },
                {
                    id: 8, 
                    name: 'Lois G. Wynn',
                    designation: 'Developer',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad ne nec dolore oblique nusquam.',
                    facebookLink: 'https://www.facebook.com/',
                    instagramLink: 'https://www.instagram.com/',
                    twitterLink: 'https://twitter.com/',
                    websiteLink: 'https://www.facebook.com', 
                    url: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/speaker-6-350x350.jpg',
                },
                {
                    id: 9, 
                    name: 'Karen A. Harris',
                    designation: 'model',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad ne nec dolore oblique nusquam.',
                    facebookLink: 'https://www.facebook.com/',
                    instagramLink: 'https://www.instagram.com/',
                    twitterLink: 'https://twitter.com/',
                    websiteLink: 'https://www.facebook.com', 
                    url: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/speaker-5-350x350.jpg',
                },
                {
                    id: 10, 
                    name: 'Ece Demir',
                    designation: 'journalist',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad ne nec dolore oblique nusquam.',
                    facebookLink: 'https://www.facebook.com/',
                    instagramLink: 'https://www.instagram.com/',
                    twitterLink: 'https://twitter.com/',
                    websiteLink: 'https://www.facebook.com', 
                    url: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/speaker-4-350x350.jpg',
                },
                {
                    id: 11, 
                    name: 'Diana Hoch',
                    designation: 'ceo &amp; founder',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad ne nec dolore oblique nusquam.',
                    facebookLink: 'https://www.facebook.com/',
                    instagramLink: 'https://www.instagram.com/',
                    twitterLink: 'https://twitter.com/',
                    websiteLink: 'https://www.facebook.com', 
                    url: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/speaker-2-350x350.jpg',
                },
                {
                    id: 12, 
                    name: 'Lara Norris',
                    designation: 'scientist',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad ne nec dolore oblique nusquam.',
                    facebookLink: 'https://www.facebook.com/',
                    instagramLink: 'https://www.instagram.com/',
                    twitterLink: 'https://twitter.com/',
                    websiteLink: 'https://www.facebook.com', 
                    url: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/speaker-1-350x350.jpg',
                }
            ],
        }),
        methods: {
            async getSpeaker(id){
                localStorage.setItem("speakerId", id);
            }
        }
    }
</script>
<template>
    <section id="eventStatus" class="py-9"> 
        <div class="container--fluid">
            <v-row
                class="mx-0"
            >
                <v-col
                    cols="12"
                    md="4"
                    sm="4"
                    xs="12"
                    v-for="status in statuses"
                    :key="status.id"
                >
                    <v-hover v-slot="{ hover }">
                        <NuxtLink to="Events"> 
                            <v-img
                                height="238px"
                                :src="status.url"
                                class="rounded-lg"
                            >
                                <div
                                    width= "100%"
                                    height="100%"
                                    class="img-div rounded-lg pa-3"
                                    v-bind:class= "{ 'on-hover' : hover}" 
                                > 
                                    <div
                                        class="text-h4 rounded-lg white--text text-uppercase d-flex flex-column justify-center align-center img-text-div"
                                    >
                                        {{status.name}}
                                        <br />
                                        <strong>Events</strong>
                                    </div>
                                </div>
                            </v-img>
                        </NuxtLink>
                    </v-hover>
                </v-col>
            </v-row>
        </div>
    </section>
</template>

<script>
    export default {
        name: 'EventStatus', 
        data: () => ({
            statuses: [
                {
                    id: 1, 
                    name: 'Upcomming',
                    url: require('../assets/Images/EventStatus/EventStatus1.png')
                },
                {
                    id: 2, 
                    name: 'Showing',
                    url: require('../assets/Images/EventStatus/EventStatus2.png')
                },
                {
                    id: 3, 
                    name: 'Expired',
                    url: require('../assets/Images/EventStatus/EventStatus3.png')
                }
            ]
        }),
        methods:{
            async goToSearchPage(){

            }
        }
    }
</script>
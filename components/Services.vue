<template>
    <section id="services" class="py-9">
        <div class="container--fluid my-9">
            <div class="section-title text-center py-9">
                <div class="text-h3">
                    Why Choose <span class="yellowish--text">Eventchamp?</span>
                </div>
                <div class="section-divider d-flex align-center justify-center my-7"> 
                    <v-divider></v-divider>
                    <v-icon
                        class="mx-2"
                        
                        color="grey lighten-2"
                    >
                        mdi-cube-outline
                    </v-icon>
                    <v-divider></v-divider>
                </div>
                <div class="text-center mb-9">
                    <div class="subtitle-1 font-weight-regular grey--text lighten-1">Because our digital story started with our dreams integrated manually.</div>
                </div>
            </div>
            <div class="section-content pb-9">
                <v-row class="mx-0 mb-5">
                    <v-col
                        cols="12"
                        md="3"
                        sm="6"
                        xs="12" 
                        v-for="service1 in services1"
                        :key="service1.id"
                    >
                        <v-card
                            class="text-center pa-1 card-div"
                            elevation="0"
                        >
                            <div
                                class="d-flex justify-center align-center card-icon-div rounded-circle mx-auto mb-5"                                
                            >
                                <v-icon
                                    x-large
                                    color="yellowish"
                                >
                                    {{service1.icon}}
                                </v-icon>
                            </div>
                            <v-card-title 
                                class="yellowish--text justify-center text-h6 pb-2"
                            >
                                {{service1.title}}
                            </v-card-title>
                            <v-card-text
                                class="text-p black--text text--secondary px-0"
                            >
                                {{service1.description}}
                            </v-card-text>
                        </v-card>
                    </v-col>
                </v-row>
                <div
                    class="text-h5 black--text text--primary text-center py-9"
                >
                    “Page builder allow you to <strong>build</strong> custom sites without touching a line of code. <strong>Drag and drop!</strong>”
                </div>
                <v-row class="mx-0 my-5">
                    <v-col
                        cols="12"
                        md="3"
                        sm="6"
                        xs="12" 
                        v-for="service2 in services2"
                        :key="service2.id"
                    >
                        <v-card
                            class="text-center pa-1 card-div"
                            elevation="0"
                        >
                            <div
                                class="d-flex justify-center align-center card-icon-div rounded-circle mx-auto mb-5"                                
                            >
                                <v-icon
                                    x-large
                                    color="yellowish"
                                >
                                    {{service2.icon}}
                                </v-icon>
                            </div>
                            <v-card-title 
                                class="yellowish--text justify-center text-h6 pb-2"
                            >
                                {{service2.title}}
                            </v-card-title>
                            <v-card-text
                                class="text-p black--text text--secondary px-0"
                            >
                                {{service2.description}}
                            </v-card-text>
                        </v-card>
                    </v-col>
                </v-row>
            </div>
        </div>
    </section>
</template>

<script>
    export default {
        name: 'Services', 
        data: () => ({
            services1:[
                {
                    id: 1,
                    title: 'MULTIPLE EVENTS', 
                    description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas et ultrices massa, sed porta dui.', 
                    icon: 'mdi-calendar-outline', 
                },
                {
                    id: 2,
                    title: 'EVENT MANAGEMENT', 
                    description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas et ultrices massa, sed porta dui.', 
                    icon: 'mdi-playlist-edit', 
                },
                {
                    id: 3,
                    title: 'PAYMENT GATEWAYS', 
                    description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas et ultrices massa, sed porta dui.', 
                    icon: 'mdi-credit-card-outline', 
                },
                {
                    id: 4,
                    title: 'VENUE MANAGEMENT', 
                    description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas et ultrices massa, sed porta dui.', 
                    icon: 'mdi-home-city-outline', 
                },
            ],
            services2:[
                {
                    id: 1,
                    title: 'SPEAKER MANAGEMENT', 
                    description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas et ultrices massa, sed porta dui.', 
                    icon: 'mdi-account-supervisor-outline', 
                },
                {
                    id: 2,
                    title: 'MULTILINGUAL SUPPORT', 
                    description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas et ultrices massa, sed porta dui.', 
                    icon: 'mdi-translate', 
                },
                {
                    id: 3,
                    title: 'PAGE BUILDER', 
                    description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas et ultrices massa, sed porta dui.', 
                    icon: 'mdi-cube-outline', 
                },
                {
                    id: 4,
                    title: 'THEME CUSTOMIZER', 
                    description: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Maecenas et ultrices massa, sed porta dui.', 
                    icon: 'mdi-tune-vertical', 
                },
            ],
        }),
    }
</script>
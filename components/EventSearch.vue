<template>
    <section id="eventSearch" class="py-9">
        <div class="container--fluid">
            <v-form>
                <v-row class="align-center">
                    <v-col
                        cols="12"
                        md="2"
                        sm="12"
                    >
                        <div class="text-h6">Event Search: </div>
                    </v-col>
                    <v-col
                        cols="12"
                        md="10"
                        sm="12"
                        class="px-md-0"
                    >
                        <v-row class="mx-0">
                            <v-col
                                cols="12"
                                md="2"
                                sm="6"
                                xs="12" 
                                class="px-md-1"
                            >
                                <v-text-field
                                    v-model="searchText"
                                    autocomplete="off"
                                    placeholder="e.g. event, meetup"
                                    label="Event"
                                    outlined
                                >
                                </v-text-field>
                            </v-col>
                            <v-col
                                cols="12"
                                md="2"
                                sm="6"
                                xs="12" 
                                class="px-md-1"
                            >
                                <v-select
                                    v-model="category"
                                    :items="categories"
                                    item-text="cat"
                                    item-value="id"
                                    label="Category"
                                    :menu-props="{ bottom: true, offsetY: true }"
                                    outlined
                                ></v-select>
                            </v-col>
                            <v-col
                                cols="12"
                                md="2"
                                sm="6"
                                xs="12" 
                                class="px-md-1"
                            >
                                <v-select
                                    v-model="location"
                                    :items="locations"
                                    item-text="loc"
                                    item-value="id"
                                    label="Location"
                                    :menu-props="{ bottom: true, offsetY: true }"
                                    outlined
                                ></v-select>
                            </v-col>
                            <v-col
                                cols="12"
                                md="2"
                                sm="6"
                                xs="12" 
                                class="px-md-1"
                            >
                                <v-select
                                    v-model="status"
                                    :items="statuses"
                                    item-text="status"
                                    item-value="id"
                                    label="Status"
                                    :menu-props="{ bottom: true, offsetY: true }"
                                    outlined
                                ></v-select>
                            </v-col>
                            <v-col
                                cols="12"
                                md="2"
                                sm="6"
                                xs="12" 
                                class="px-md-1"
                            >
                                <v-menu
                                    v-model="menu"
                                    :close-on-content-click="false"
                                    :nudge-right="40"
                                    transition="scale-transition"
                                    offset-y
                                    min-width="auto"
                                >
                                    <template v-slot:activator="{ on, attrs }">
                                        <v-text-field
                                            v-model="date"
                                            label="Start Date"
                                            v-bind="attrs"
                                            v-on="on"
                                            outlined
                                        ></v-text-field>
                                    </template>
                                    <v-date-picker
                                        v-model="date"
                                        @input="menu = false"
                                    ></v-date-picker>
                                </v-menu>
                            </v-col>
                            <v-col
                                cols="12"
                                md="2"
                                sm="6"
                                xs="12" 
                            >
                                <NuxtLink to="Events">
                                    <v-btn
                                        class="btn-yellowish-style"
                                        block
                                        x-large
                                        elevation="0"
                                    >
                                        Search
                                    </v-btn>
                                </NuxtLink>
                            </v-col>
                        </v-row>
                    </v-col>
                </v-row>
            </v-form>
        </div>
    </section>
</template>

<script>
    export default {
        name: 'EventSearch',
        data: ()=> ({
            searchText: '', 
            category: null, 
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
            location: null,
            locations: [
                {
                    id: 1, 
                    loc: 'London',
                },
                {
                    id: 2, 
                    loc: 'England',
                },
                {
                    id: 3, 
                    loc: 'USA',
                },
                {
                    id: 4, 
                    loc: 'Manchester',
                },
                {
                    id: 5, 
                    loc: 'France',
                },
                {
                    id: 6, 
                    loc: 'Istanbul',
                },
                {
                    id: 7, 
                    loc: 'California',
                },
                {
                    id: 8, 
                    loc: 'Texas',
                },
                {
                    id: 9, 
                    loc: 'Madrid',
                },
            ],
            status: null,
            statuses: [
                {
                    id: 1, 
                    status: 'Upcomming', 
                },
                {
                    id: 2, 
                    status: 'Showing', 
                },
                {
                    id: 3, 
                    status: 'Expired', 
                }
            ],

            // date: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
            date: null, 
            menu: false,
        }),
    }
</script>

<style>
    .v-picker__title.primary{
        background-color: #fb0 !important; 
    }
    .v-date-picker-table__current{
        background-color: #fb0 !important; 
        border-color: #fb0 !important; 
    }
    .v-btn--active{
        background-color: #fb0 !important; 
        border-color: #fb0 !important; 
    }
    .v-application .primary, .v-application .accent{
        background-color: #fb0 !important;
        border-color: #fb0 !important;
        color: #fff !important;
    }
</style>
<template>
    <div class="subPageContent">
        <div class="container--fluid">
            <v-row>
                <v-col
                    col="12"
                    md="8"
                    sm="12"
                >
                    <div 
                        class="white content-div pa-8 rounded-lg"
                    >
                        <div
                            class="py-3 text-h6 mb-5"
                            style="border-bottom: 1px solid #eaeaea"
                        >
                            Post an Event
                        </div>
                        <v-form
                            ref="form"
                            v-model="valid"
                            lazy-validation
                            class="mt-9"
                        >
                            <v-text-field
                                v-model="title"
                                :rules="inputRules"
                                label="Title"
                                outlined
                                required
                            ></v-text-field>

                            <v-select
                                v-model="category"
                                :items="categories"
                                item-text= "cat"
                                item-value= "id"
                                :rules="[v => !!v || 'Item is required']"
                                label="Blog Category"
                                required
                                outlined
                            ></v-select>

                            <client-only>
                                <vue-editor 
                                    placeholder="Blog Description..." 
                                    v-model="description1" 
                                    required
                                    class="mb-5"
                                ></vue-editor>
                            </client-only>

                            <v-file-input
                                label="Blog Banner Image"
                                prepend-icon=""
                                prepend-inner-icon="mdi-camera"
                                outlined
                                required
                            ></v-file-input>

                            <!-- <v-textarea
                                v-model="description2"
                                label="Description (Add more)"
                                outlined
                                rows="4"
                            ></v-textarea> -->

                            <client-only>
                                <vue-editor 
                                    placeholder="Blog Description... (Add More)" 
                                    v-model="description2" 
                                    required
                                    class="mb-5"
                                ></vue-editor>
                            </client-only>

                            <v-file-input
                                v-model="blogImages"
                                counter
                                label="Blog Images"
                                prepend-icon=""
                                prepend-inner-icon="mdi-camera"
                                multiple
                                outlined
                                :show-size="1000"
                            >
                                <template v-slot:selection="{ index, text }">
                                    <v-chip
                                        v-if="index < 2"
                                        color="yellowish"
                                        dark
                                        label
                                        small
                                    >
                                        {{ text }}
                                    </v-chip>

                                    <span
                                        v-else-if="index === 2"
                                        class="text-overline grey--text text--darken-3 mx-2"
                                    >
                                        +{{ blogImages.length - 2 }} File(s)
                                    </span>
                                </template>
                            </v-file-input>
                            
                            <v-menu
                                v-model="blogDatePicker"
                                :close-on-content-click="false"
                                :nudge-right="40"
                                transition="scale-transition"
                                offset-y
                                min-width="auto"
                            >
                                <template v-slot:activator="{ on, attrs }">
                                    <v-text-field
                                        v-model="date"
                                        label="Date"
                                        prepend-inner-icon="mdi-calendar-outline"
                                        outlined
                                        v-bind="attrs"
                                        v-on="on"
                                    ></v-text-field>
                                </template>
                                <v-date-picker
                                    v-model="date"
                                    @input="blogDatePicker = false"
                                >
                                </v-date-picker>
                            </v-menu>

                            <v-select
                                v-model="tag"
                                :items="tags"
                                item-text= "tag"
                                item-value= "id"
                                :rules="[v => !!v || 'Tag is required']"
                                label="Tags"
                                required
                                outlined
                                multiple
                                chips
                            ></v-select>

                            <v-text-field
                                v-model="authorName"
                                :rules="inputRules"
                                label="Author Name"
                                outlined
                                required
                            ></v-text-field>

                            <v-textarea
                                v-model="authorDescription"
                                :rules="inputRules"
                                label="author Description"
                                outlined
                                required
                                rows="4"
                            ></v-textarea>

                            <v-text-field
                                v-model="authorFacebookLink"
                                label="Authors' Facebook Link"
                                outlined
                            ></v-text-field>

                            <v-text-field
                                v-model="authorInstagramLink"
                                label="Authors' Instagram Link"
                                outlined
                            ></v-text-field>

                            <v-text-field
                                v-model="authorTwitterLink"
                                label="Authors' Twitter Link"
                                outlined
                            ></v-text-field>

                            <v-text-field
                                v-model="authorYoutubeLink"
                                label="Authors' Youtube Link"
                                outlined
                            ></v-text-field>

                            <v-btn
                                :disabled="!valid"
                                large
                                class="mr-4 btn-yellowish-style"
                                @click="validate"
                            >
                                Post Blog
                            </v-btn>

                            <v-btn
                                color="grey darken-1"
                                class="mr-4 white--text"
                                large
                                @click="reset"
                            >
                                Cancel
                            </v-btn>

                        </v-form>
                    </div>
                </v-col>
                <v-col
                    col="12"
                    md="4"
                    sm="12"
                >
                    <SidebarAdvertise /> 
                </v-col>
            </v-row>
        </div>

        <v-snackbar
            v-model="blogSnackbar"
            timeout="2000"
            color="primary"
        >
            Congrtualations!!! Your Blog Submitted Successfully!!!

            <template v-slot:action="{ attrs }">
                <v-btn
                    color="white"
                    text
                    v-bind="attrs"
                    @click="blogSnackbar = false" 
                >
                Close
                </v-btn>
            </template>
        </v-snackbar>
    </div>
</template>

<script>
    import SidebarAdvertise from '../components/SidebarAdvertise.vue'

    let VueEditor;
    if (process.browser) {
        VueEditor = require('vue2-editor').VueEditor
    }

    export default {
        name: 'PostEvent',
        data: () => ({
            valid: true,
            inputRules: [
                v => !!v || 'This Field is required',
            ],
            title: '',
            description1: '',
            description2: '',
            blogImages: [],
            authorName: '',
            authorDescription: '', 
            authorFacebookLink: '',
            authorInstagramLink: '',
            authorTwitterLink: '',
            authorYoutubeLink: '',
            tag: null, 
            tags: [
                {
                    id: 1, 
                    tag: 'Art', 
                },
                {
                    id: 2, 
                    tag: 'Business', 
                },
                {
                    id: 3, 
                    tag: 'Concert', 
                },
                {
                    id: 4, 
                    tag: 'Conferrence', 
                },
                {
                    id: 5, 
                    tag: 'Education', 
                },
                {
                    id: 6, 
                    tag: 'Festival', 
                },
                {
                    id: 7, 
                    tag: 'Food', 
                },
                {
                    id: 8, 
                    tag: 'Micellaneous', 
                },
                {
                    id: 9, 
                    tag: 'Nightlife', 
                },
                {
                    id: 10, 
                    tag: 'Sports', 
                },
                {
                    id: 11, 
                    tag: 'Technology', 
                },
                {
                    id: 12, 
                    tag: 'Travel', 
                },
                {
                    id: 13, 
                    tag: 'Wedding', 
                },
            ],
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
            date: (new Date(Date.now() - (new Date()).getTimezoneOffset() * 60000)).toISOString().substr(0, 10),
            menu: false,
            modal: false,
            blogDatePicker: false,

            pageIsMounted: false,
            isSSR: process.server ? true : false, 
            blogSnackbar: false, 
        }),
        methods: {
            validate () {
                if(this.$refs.form.validate()){
                    this.blogSnackbar = true; 
                }
            },
            reset () {
                this.$refs.form.reset()
            },
            resetValidation () {
                this.$refs.form.resetValidation()
            },
        },
    }
</script>

<style scoped>
    .v-file-input .v-input__prepend-outer{
        display: none !important; 
    }
</style>

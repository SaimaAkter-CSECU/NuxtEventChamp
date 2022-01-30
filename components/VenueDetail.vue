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
                        class="content-div"
                    >
                        <!-- Venue Details -->
                        <div class="white pa-0 rounded-lg">
                            <div class="venue-details">
                            <v-img
                                :src="venue.url"
                                max-height="650px"
                            ></v-img>
                            <div
                                class="pa-8"
                            >
                                <div 
                                    class="text-p font-weight-normal text-justify mb-7" 
                                    v-html="venue.description"
                                    style="line-height: 1.7" 
                                >
                                </div>
                                <div>
                                    <div
                                        class="d-flex align-center flex-wrap mb-9"
                                    >
                                        <div
                                            class="category-tags"
                                            v-for="category in categories"
                                            :key="category.id"
                                        >
                                            <NuxtLink :to="{path: '../Location/'+category.category }">
                                                <v-btn
                                                    class="mr-2 font-weight-normal"
                                                    small
                                                    tile
                                                    elevation="0"
                                                >
                                                    {{category.category}}
                                                </v-btn>
                                            </NuxtLink>
                                        </div>
                                    </div>
                                    <div 
                                        class="subtitle-2 text-uppercase mb-3 v-btn--fab-title"
                                    >
                                        Share This Post 
                                    </div>
                                    <div
                                        class="d-flex align-enter mb-5"
                                    >
                                        <v-btn
                                            class="mr-1"
                                            fab
                                            small
                                            elevation="0"
                                        >
                                            <v-icon 
                                                class="white--text" 
                                            >
                                                mdi-alpha-f
                                            </v-icon>
                                        </v-btn>
                                        <v-btn
                                            class="mx-1"
                                            fab
                                            small
                                            elevation="0"
                                        >
                                            <v-icon 
                                                class="white--text" 
                                                small
                                            >
                                                mdi-twitter
                                            </v-icon>
                                        </v-btn>
                                        <v-btn
                                            class="mx-1"
                                            fab
                                            small
                                            elevation="0"
                                        >
                                            <v-icon 
                                                class="white--text" 
                                                small
                                            >
                                                mdi-whatsapp
                                            </v-icon>
                                        </v-btn>
                                        <v-btn
                                            class="mx-1"
                                            fab
                                            small
                                            elevation="0"
                                        >
                                            <v-icon
                                                class="white--text" 
                                                small
                                            >
                                                mdi-email-outline
                                            </v-icon>
                                        </v-btn>
                                    </div>
                                </div>
                            </div>
                        </div>
                        </div>

                        <!-- Photos -->
                        <div 
                            class="photos-div white rounded-lg my-8"
                            v-show="venue.photos"
                        > 
                            <div
                                class="py-7 pl-8 text-h6"
                                style="border-bottom: 1px solid #eaeaea"
                            >
                                Photos
                            </div>
                            <div
                                class="pa-8"
                            >
                                <v-row
                                    class="align-center"
                                >
                                    <v-col
                                        col="12"
                                        md="4"
                                        sm="6"
                                        xs="12"
                                        class="pa-0"
                                        v-for="photos in venue.photos"
                                        :key="photos.id"
                                    >
                                        

                                        <v-img
                                            :src="photos.url"
                                            width="100%"
                                        >
                                            <div 
                                                class="overlay"
                                            ></div>
                                        </v-img>
                                    </v-col>
                                </v-row>
                                <!-- <no-ssr>
                                            <LightGallery
                                                :images="event.photos"
                                                :index="event.photos.id"
                                                :disable-scroll="true"
                                                @close="index = null"
                                            />
                                            <ul>
                                                <li
                                                    v-for="photos in event.photos"
                                                    :key="photos.id"
                                                    @click="index = photos.id"
                                                >
                                                    <img :src="photos.url">
                                                </li>
                                            </ul>
                                        </no-ssr> -->
                            </div>
                        </div>
                        
                        
                        <!-- Add Comment -->
                        <div class="white rounded-lg my-8">
                            <div
                                class="py-7 pl-8 text-h6"
                                style="border-bottom: 1px solid #eaeaea"
                            >
                                Leave a Comment
                            </div>
                            <div
                                class="pa-8"
                            >
                                <v-form
                                    ref="form"
                                    v-model="valid"
                                    lazy-validation
                                >
                                    <v-row>
                                        <v-col
                                            col="12"
                                            sm="12"
                                            xs="12"
                                        >
                                            <v-textarea
                                                name="commentField" 
                                                :rules="inputRules"
                                                rows="4"
                                                label="Your Comment"
                                                outlined
                                            ></v-textarea>
                                        </v-col>
                                        <v-col
                                            col="12"
                                            md="4"
                                            sm="6"
                                            xs="12"
                                            class="py-0"
                                        >
                                            <v-text-field
                                                v-model="name"
                                                :rules="inputRules"
                                                label="Name"
                                                required
                                                outlined
                                            ></v-text-field>
                                        </v-col>
                                        <v-col
                                            col="12"
                                            md="4"
                                            sm="6"
                                            xs="12"
                                            class="py-0"
                                        >
                                            <v-text-field
                                                v-model="email"
                                                :rules="emailRules"
                                                label="Email"
                                                required
                                                outlined
                                            ></v-text-field>
                                        </v-col>
                                        <v-col
                                            col="12"
                                            md="4"
                                            sm="6"
                                            xs="12"
                                            class="py-0"
                                        >
                                            <v-text-field
                                                v-model="websiteUrl"
                                                label="Website URL"
                                                outlined
                                            ></v-text-field>
                                        </v-col>
                                        <v-col
                                            col="12"
                                            md="12"
                                            sm="12"
                                            xs="12"
                                            class="pt-0"
                                        >
                                            <v-checkbox
                                                v-model="checkbox"
                                                label="Save my name, email and website in this browser for the next time I comment."
                                            ></v-checkbox>
                                        </v-col>
                                    </v-row>

                                    <v-btn
                                        :disabled="!valid"
                                        class="my-5 mr-4 text-uppercase btn-yellowish-style rounded-md"
                                        @click="validate"
                                        elevation="0"
                                        x-large 
                                    >
                                        Post Comment
                                    </v-btn>
                                </v-form>
                            </div>
                        </div>
                    </div>

                    
                </v-col>

                <v-col
                    col="12"
                    md="4"
                    sm="12"
                >
                    <SidebarVenueDetails :venue="venues[0]"  ></SidebarVenueDetails>
                    <SidebarVenueSponsor :venue="venues[0]" ></SidebarVenueSponsor>
                </v-col>
            </v-row>

            <v-row>
                <v-col
                    col="12"
                    md="12"
                >
                    <VenueEvents />
                </v-col>
            </v-row>

            <v-row>
                <v-col
                    col="12"
                    md="12"
                >
                    <RelatedVenues />
                </v-col>
            </v-row>
        </div>
    </div>
</template>

<script>
    import SidebarVenueDetails from './SidebarVenueDetails.vue'
    import SidebarVenueSponsor from './SidebarVenueSponsor.vue'
    import VenueEvents from './VenueEvents.vue'
    import RelatedVenues from './RelatedVenues.vue' 

    export default {
        name: 'VenueDetail',
        data: () => ({
            venues: [
                {
                    id: 1, 
                    title: 'Oxnard Beach',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has. Sed ad dicam platonem, mea eros illum elitr id, ei has similique constituto. Ea movet saperet rationibus sit, pri autem aliquip invidunt an. Consetetur omittantur consequuntur eos et. <strong> Eleifend praesent iudicabit no mea, tollit persequeris ex pri, tota splendide voluptaria in pri.</strong> Ad per tale aliquip, ei sit viris commune albucius. Eos aliquip scaevola ut, eum alii mentitum prodesset no, his ne suas atomorum. Et numquam deleniti ponderum vis, quod error at mei. Novum blandit adolescens sea te. Ea eum cetero scaevola.<br /><br />In his meis porro viris, illud imperdiet reprimique et vim. Feugiat atomorum reprehendunt vix ei, ei facete regione pri. Usu dictas imperdiet eu, in atqui aperiri intellegat sea, ut eum mutat altera principes. Te sit quaeque oportere, has modus inani ceteros ad. Impedit blandit deseruisse duo ea, ne graecis deleniti incorrupte usu. Ut mei splendide accommodare. An pri iisque meliore, eam ei splendide eloquentiam philosophia. <u>Ne per meis eleifend electram.</u> Ne eam porro aliquam invidunt. Minim docendi eloquentiam cum ad. Quo ea mazim ubique, ex est fuisset blandit scaevola. Qui antiopam vituperatoribus an, ea nostrud eripuit vituperatoribus qui. In eam diam nominati, per ea alia luptatum. <span class="yellowish--text">Nam habemus electram democritum ut.</span> Mei ea omnium admodum intellegat. Habeo atqui molestiae at mei, an nec ridens consequuntur. Quem nulla cum ei, his ipsum apeirian no, per at eius iriure aperiri. Sed dicam interesset ei. Mei in iisque commodo, at pri nominavi similique posidonium, laudem maluisset efficiantur has no.<br/><br /><br />His verterem consectetuer consequuntur ne, no virtute atomorum usu. <b> Eu quo nemore causae tacimates, eos viderer persequeris an.</b> Cu molestie consulatu qui. Natum labores perfecto no ius, pri dico mundi inciderint id. Ei usu dico libris postea. Cu graeco doctus splendide qui, ei eum probo regione.', 
                    weekdays: '09:00 - 22:30', 
                    saturday: '09:00 - 23:59', 
                    sunday: 'Closed', 

                    location: 'Callifornia', 
                    address: 'Harbiye Mahallesi, Darülbedai Caddesi No:3, 34367 Şişli/İstanbul',
                    catId: 9,
                    category: 'Beach', 
                    
                    phone: '0674 987 665',
                    email: 'event@gloriathemes.com', 
                    website: 'www.website.com',
                    
                    url: require('../assets/Images/LatestPost/LatestPost1.png'),

                    eventFacebook: 'http://www.facebook.com',
                    eventInstagram: 'http://www.instagram.com', 
                    eventYoutube: 'http://www.youtube.com', 
                    eventTwitter: 'http://www.facebook.com', 
                    whishCount: 7, 
                    
                    photos: [
                        {
                            id: 1, 
                            url : 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/event-3-350x350.jpg',
                        },
                        {
                            id: 2, 
                            url : 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/event-3-350x350.jpg',
                        },
                        {
                            id: 3, 
                            url : 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/event-3-350x350.jpg',
                        },
                        {
                            id: 4, 
                            url : 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/event-3-350x350.jpg',
                        },
                        {
                            id: 5, 
                            url : 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/event-3-350x350.jpg',
                        },
                        {
                            id: 6, 
                            url : 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/event-3-350x350.jpg',
                        },
                        {
                            id: 7, 
                            url : 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/event-3-350x350.jpg',
                        },
                        {
                            id: 8, 
                            url : 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/event-3-350x350.jpg',
                        },
                        {
                            id: 9, 
                            url : 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/event-3-350x350.jpg',
                        }
                    ],
                    sponsors: [
                        {
                            id: 1,
                            link: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/sponsor-1-250x220.jpg',
                            img: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/sponsor-1-250x220.jpg',
                        },
                        {
                            id: 2,
                            link: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/sponsor-1-250x220.jpg',
                            img: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/sponsor-1-250x220.jpg',
                        },
                        {
                            id: 3,
                            link: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/sponsor-1-250x220.jpg',
                            img: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/sponsor-1-250x220.jpg',
                        },
                        {
                            id: 4,
                            link: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/sponsor-1-250x220.jpg',
                            img: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/sponsor-1-250x220.jpg',
                        },
                        {
                            id: 5,
                            link: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/sponsor-1-250x220.jpg',
                            img: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/sponsor-1-250x220.jpg',
                        },
                        {
                            id: 6,
                            link: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/sponsor-1-250x220.jpg',
                            img: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/sponsor-1-250x220.jpg',
                        },
                    ],
                }
            ], 
            venue: [],
            categories: [
                {
                    id: 1,
                    category: 'Events'
                },
                {
                    id: 2,
                    category: 'Meeting'
                },
                {
                    id: 3,
                    category: 'Conferrence'
                },
                {
                    id: 4,
                    category: 'Venue'
                }
                ,
                {
                    id: 5,
                    category: 'Speakers'
                }
            ],

            valid: true,
            commentField: '', 
            name: '',
            inputRules: [
                v => !!v || 'This Field is Required',
                v => (v && v.length <= 10) || 'Name must be less than 10 characters',
            ],
            email: '',
            emailRules: [
                v => !!v || 'E-mail is Required',
                v => /.+@.+\..+/.test(v) || 'E-mail must be valid',
            ],
            websiteUrl: '', 
            checkbox: false,
        }),
        methods: {
            async getVenue(id){
                localStorage.setItem("venueId", id);
                console.log(localStorage); 
            },
            async validate () {
                this.$refs.form.validate()
            },
        },
        mounted() {
            // this.venue = this.venue.find(x => x.id == localStorage.getItem('venueId') ); 
            // console.log(this.event[0]);
            this.venue = this.venues[0]; 
            console.log(this.venue); 
            console.log(this.venue.photos); 
            console.log(this.venue.location); 
            console.log(this.venue.sponsors); 
        },
    }
</script>
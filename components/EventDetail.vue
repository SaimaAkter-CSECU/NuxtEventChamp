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
                        <!-- Event Details -->
                        <div class="white pa-0 rounded-lg">
                            <div class="event-details">
                            <v-img
                                :src="event.url"
                                height="650px"
                            ></v-img>
                            <div
                                class="pa-8"
                            >
                                <div 
                                    class="text-p font-weight-normal text-justify mb-7" 
                                    v-html="event.description"
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
                                            <NuxtLink :to="{path: '../Category/'+(category.category).charAt(0).toUpperCase()+(category.category).slice(1) }">
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
                            v-show="event.photos"
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
                                        v-for="photos in event.photos"
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
                        
                        <!-- Related Blogs -->
                        <!-- <div class="white rounded-lg my-8">
                            <div
                                class="py-7 pl-8 text-h6"
                                style="border-bottom: 1px solid #eaeaea"
                            >
                                Related Events
                            </div>
                            <div
                                class="pa-8"
                            >
                                <v-row
                                    class="align-center"
                                >
                                    <v-col
                                        col="12"
                                        sm="6"
                                        xs="12"
                                        v-for="relatedBlog in relatedBlogs"
                                        :key="relatedBlog.id"
                                    >
                                        <v-card
                                            elevation="0"
                                        >
                                            <v-img
                                                :src="relatedBlog.url"
                                                class="rounded-lg"
                                                style="cursor:pointer;"
                                            >
                                                <div
                                                    class="d-flex align-end pa-7"
                                                    style="width:100%; height: 100%;"
                                                >
                                                    <NuxtLink :to="{path: '../Category/'+(relatedBlog.category).charAt(0).toUpperCase()+(relatedBlog.category).slice(1) }">
                                                        <v-btn
                                                            class="rounded-pill yellowish--text text-uppercase" 
                                                            color="white"
                                                            style="font-weight: 400; letter-spacing: 0.25px" 
                                                        >
                                                            {{relatedBlog.category}}
                                                        </v-btn>
                                                    </NuxtLink>
                                                </div>
                                            </v-img>
                                            <v-card-title
                                                class="px-0 pb-0 d-inline-block text-truncate"
                                                style="max-width: 100%"
                                                @click="geTBlog(relatedBlog.id)"
                                            >
                                                <NuxtLink :to="{path: '../Detail/'+(relatedBlog.title).split(' ').join('-') }">
                                                    {{relatedBlog.title}}
                                                </NuxtLink>
                                            </v-card-title>
                                            <v-card-text
                                                class="px-0 pt-0 mb-3"
                                            >
                                                <div class="d-flex align-center">
                                                    <div
                                                        class="mr-4 d-flex align-center"
                                                    >
                                                        <v-icon
                                                            color="yellowish"
                                                            small
                                                            class="mr-2"
                                                        >
                                                            mdi-calendar-blank-outline
                                                        </v-icon>
                                                        <span class="body-2">
                                                            {{relatedBlog.date}}
                                                        </span>
                                                    </div>
                                                    <div
                                                        class="d-flex align-center"
                                                    >
                                                        <v-icon
                                                            color="yellowish"
                                                            small
                                                            class="mr-2"
                                                        >
                                                            mdi-chat-outline
                                                        </v-icon>
                                                        <span class="body-2">
                                                            {{relatedBlog.comment}} comment 
                                                        </span>
                                                    </div>
                                                </div>
                                            </v-card-text>
                                        </v-card>
                                    </v-col>
                                </v-row>
                            </div>
                        </div> -->
                        
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
                    <SidebarEventDetails :event="event" ></SidebarEventDetails>
                    <SidebarEventSponsor :event="event"  ></SidebarEventSponsor>
                </v-col>
            </v-row>

            <v-row>
                <v-col
                    col="12"
                    md="12"
                >
                    <RelatedEvents />
                </v-col>
            </v-row>
        </div>
    </div>
</template>

<script>
    import SidebarEventDetails from './SidebarEventDetails.vue'
    import SidebarEventSponsor from './SidebarEventSponsor.vue'
    import RelatedEvents from './RelatedEvents.vue' 

    export default {
        name: 'EventDetail',
        data: () => ({
            index: null, 
            event: [
                {
                    id: 1, 
                    title: 'Top 20 Event and Conference Countries',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has. Sed ad dicam platonem, mea eros illum elitr id, ei has similique constituto. Ea movet saperet rationibus sit, pri autem aliquip invidunt an. Consetetur omittantur consequuntur eos et. <strong> Eleifend praesent iudicabit no mea, tollit persequeris ex pri, tota splendide voluptaria in pri.</strong> Ad per tale aliquip, ei sit viris commune albucius. Eos aliquip scaevola ut, eum alii mentitum prodesset no, his ne suas atomorum. Et numquam deleniti ponderum vis, quod error at mei. Novum blandit adolescens sea te. Ea eum cetero scaevola.<br /><br />In his meis porro viris, illud imperdiet reprimique et vim. Feugiat atomorum reprehendunt vix ei, ei facete regione pri. Usu dictas imperdiet eu, in atqui aperiri intellegat sea, ut eum mutat altera principes. Te sit quaeque oportere, has modus inani ceteros ad. Impedit blandit deseruisse duo ea, ne graecis deleniti incorrupte usu. Ut mei splendide accommodare. An pri iisque meliore, eam ei splendide eloquentiam philosophia. <u>Ne per meis eleifend electram.</u> Ne eam porro aliquam invidunt. Minim docendi eloquentiam cum ad. Quo ea mazim ubique, ex est fuisset blandit scaevola. Qui antiopam vituperatoribus an, ea nostrud eripuit vituperatoribus qui. In eam diam nominati, per ea alia luptatum. <span class="yellowish--text">Nam habemus electram democritum ut.</span> Mei ea omnium admodum intellegat. Habeo atqui molestiae at mei, an nec ridens consequuntur. Quem nulla cum ei, his ipsum apeirian no, per at eius iriure aperiri. Sed dicam interesset ei. Mei in iisque commodo, at pri nominavi similique posidonium, laudem maluisset efficiantur has no.<br/><br /><br />His verterem consectetuer consequuntur ne, no virtute atomorum usu. <b> Eu quo nemore causae tacimates, eos viderer persequeris an.</b> Cu molestie consulatu qui. Natum labores perfecto no ius, pri dico mundi inciderint id. Ei usu dico libris postea. Cu graeco doctus splendide qui, ei eum probo regione.', 
                    status: 'Showing', 
                    startDate: 'March 1, 2021 10:30 am', 
                    endDate: 'September 15, 2023 3:30 pm', 
                    venue: 'Istanbul Event Arena', 
                    location: 'Milano', 
                    address: 'Harbiye Mahallesi, Darülbedai Caddesi No:3, 34367 Şişli/İstanbul',
                    organizer: 'Philip Young',
                    catId: 2,
                    category: 'Business', 
                    cost: '29', 
                    phone: '0674 987 665',
                    email: 'event@gloriathemes.com', 
                    remainingTickets: 0, 
                    url: require('../assets/Images/LatestPost/LatestPost1.png'),
                    eventFacebook: 'http://www.facebook.com',
                    eventInstagram: 'http://www.instagram.com', 
                    eventYoutube: 'http://www.youtube.com', 
                    eventTwitter: 'http://www.facebook.com', 
                    whishCount: 7, 
                    faqs: [
                        {
                            id: 1, 
                            question: 'Proin lacinia placerat est et euismod?',
                            answer: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse non posuere dolor, ut fermentum enim. Nullam quis molestie purus. Nam leo turpis, scelerisque in convallis ac, accumsan a lacus. Sed laoreet arcu in odio auctor commodo qisque et mi lacinia.',
                        },
                        {
                            id: 2, 
                            question: 'Proin lacinia placerat est et euismod?',
                            answer: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse non posuere dolor, ut fermentum enim. Nullam quis molestie purus. Nam leo turpis, scelerisque in convallis ac, accumsan a lacus. Sed laoreet arcu in odio auctor commodo qisque et mi lacinia.',
                        },
                        {
                            id: 3, 
                            question: 'Proin lacinia placerat est et euismod?',
                            answer: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse non posuere dolor, ut fermentum enim. Nullam quis molestie purus. Nam leo turpis, scelerisque in convallis ac, accumsan a lacus. Sed laoreet arcu in odio auctor commodo qisque et mi lacinia.',
                        },
                        {
                            id: 4, 
                            question: 'Proin lacinia placerat est et euismod?',
                            answer: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse non posuere dolor, ut fermentum enim. Nullam quis molestie purus. Nam leo turpis, scelerisque in convallis ac, accumsan a lacus. Sed laoreet arcu in odio auctor commodo qisque et mi lacinia.',
                        },
                        {
                            id: 5, 
                            question: 'Proin lacinia placerat est et euismod?',
                            answer: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Suspendisse non posuere dolor, ut fermentum enim. Nullam quis molestie purus. Nam leo turpis, scelerisque in convallis ac, accumsan a lacus. Sed laoreet arcu in odio auctor commodo qisque et mi lacinia.',
                        },
                    ],
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
            categories: [
                {
                    id: 1,
                    category: 'Lists'
                },
                {
                    id: 2,
                    category: 'News'
                },
                {
                    id: 3,
                    category: 'Events'
                },
                {
                    id: 4,
                    category: 'culture'
                }
                ,
                {
                    id: 5,
                    category: 'Meetup'
                },
                {
                    id: 6,
                    category: 'Food'
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
            async geTEvent(id){
                localStorage.setItem("eventId", id);
                console.log(localStorage); 
            },
            async validate () {
                this.$refs.form.validate()
            },
        },
        mounted() {
            // this.event = this.blogs.find(x => x.id == localStorage.getItem('eventId') ); 
            // console.log(this.event[0]);
            this.event = this.event[0]; 
            // console.log(this.event); 
            // console.log(this.event.photos); 
        },
    }
</script>
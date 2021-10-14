<template>
    <footer class="footer font-display white--text">
        <div class="footer-menu py-9">
            <div class="container--fluid mt-9">
                <v-row class="ma-0">
                    <v-col
                        cols="12"
                        md="4"
                        sm="12" 
                    >
                        <div class="text-uppercase footer-menu-title pb-3">contact</div>
                        <div class="footer-menu-content my-9">
                            <div class="">
                                <p>
                                    <v-icon 
                                        class="mr-2"
                                        color="yellowish"
                                    >
                                        mdi-map-marker-outline
                                    </v-icon>
                                    <span>Walking Street, Los Angeles, California, USA</span>
                                </p>
                                <p>
                                    <v-icon 
                                        class="mr-2"
                                        color="yellowish"
                                    >
                                        mdi-email-outline
                                    </v-icon>
                                    <span><a href="mailto:info@eventchamp.com">info@eventchamp.com</a></span>
                                </p>
                                <p>
                                    <v-icon 
                                        class="mr-2"
                                        color="yellowish"
                                    >
                                        mdi-phone-outline
                                    </v-icon>
                                    <span><a href="tel:+903126912">+90 312 69 12</a></span>
                                </p>
                            </div>
                            <div class="d-flex social-icon-div mt-9">
                                <a 
                                    href="#"
                                    class="mr-2 social-icon-outline" 
                                    circle
                                >
                                    <v-icon
                                        style="font-size: 1.625rem; "
                                    >
                                        mdi-alpha-f
                                    </v-icon>
                                </a>
                                <a 
                                    href="#"
                                    class="mr-2 social-icon-outline" 
                                    circle
                                >
                                    <v-icon
                                    >
                                        mdi-twitter
                                    </v-icon>
                                </a>
                                <a 
                                    href="#"
                                    class="mr-2 social-icon-outline" 
                                    circle
                                >
                                    <v-icon
                                    >
                                        mdi-instagram
                                    </v-icon>
                                </a>
                                <a 
                                    href="#"
                                    class="mr-1 social-icon-outline" 
                                    circle
                                >
                                    <v-icon
                                    >
                                        mdi-youtube
                                    </v-icon>
                                </a>
                            </div>
                        </div>
                    </v-col>
                    <v-col
                        cols="12"
                        md="4"
                        sm="12" 
                    >
                        <div class="text-uppercase footer-menu-title">LATEST POSTS</div>
                        <div class="footer-menu-content my-9">
                            <v-list color="transparent" class="footerLatestPosts">
                                <v-list-item 
                                    v-for="latestPost in latestPosts"
                                    :key="latestPost.id"
                                    class="pl-0"
                                >
                                    <v-row class="ma-0">
                                        <v-col
                                            cols="2"                                                                           
                                            sm="2"
                                            xs="2"
                                            class="pl-0"
                                        >
                                            <NuxtLink :to="{path: 'Events/Detail/'+(latestPost.title).split(' ').join('-')}">
                                                <v-img
                                                    :src="latestPost.url"
                                                    max-width="100%"
                                                    @click="getBlog(latestPost.id)"
                                                ></v-img>
                                            </NuxtLink>
                                        </v-col>
                                        <v-col
                                            cols="10"
                                            sm="10"
                                            xs="10"
                                            class="white--text pl-1"
                                        >
                                            <v-list-item-title 
                                                class="text-p mb-3"
                                                @click="getBlog(latestPost.id)"
                                            >
                                                <NuxtLink :to="{path: 'Events/Detail/'+(latestPost.title).split(' ').join('-')}">
                                                    {{latestPost.title}}
                                                </NuxtLink>
                                            </v-list-item-title>
                                            <v-list-item-subtitle class="white--text d-flex align-center">
                                                <v-icon
                                                    small
                                                    color="yellowish"
                                                    class="mr-1"
                                                >
                                                    mdi-calendar-blank-outline
                                                </v-icon>
                                                <span class="body-2">{{latestPost.date}}</span>
                                            </v-list-item-subtitle>
                                        </v-col>
                                    </v-row>
                                </v-list-item>
                            </v-list>
                        </div>
                    </v-col>
                    <v-col
                        cols="12"
                        md="4"
                        sm="12" 
                    >
                        <div class="text-uppercase footer-menu-title">our apps</div>
                        <div class="footer-menu-content mt-9 mb-9">
                            <div class="">
                                <p style="line-height: 1.7;">
                                    Lorem ipsum dolor sit amet, consectetur adipiscing elit. <strong>Maecenas et ultrices massa, sed porta dui</strong> lobortis tincidunt. Sed diam nonummy nibh euismod.
                                </p>
                            </div>
                            <v-row class="ma-0 app-div">
                                <v-col 
                                    cols="12"
                                    sm="6"
                                    class="pl-0"
                                >
                                    <a 
                                        href="#"
                                        class="px-4 py-3 d-flex align-center rounded-lg"
                                    >
                                        <v-icon
                                            color="white" 
                                            large
                                            class="mr-2"
                                        >
                                            mdi-apple
                                        </v-icon>
                                        <div>
                                            <p class="mb-1">Download via</p>
                                            <p class="mb-0"><strong>Apple Store</strong></p>
                                        </div>
                                    </a>
                                </v-col>
                                <v-col 
                                    cols="12"
                                    sm="6"
                                    class="pr-0"
                                >
                                    <a 
                                        href=""
                                        class="px-4 py-3 d-flex align-center rounded-lg"
                                    >
                                        <v-icon
                                            large
                                            class="mr-2"
                                        >
                                            mdi-google-play
                                        </v-icon>
                                        <div>
                                            <p class="mb-1">Download via</p>
                                            <p class="mb-0"><strong>Google Play</strong></p>
                                        </div>
                                    </a>
                                </v-col>
                            </v-row>
                            <!-- <div 
                                width="100%"
                                class="d-flex app-div mt-9"
                            >
                                <div
                                    width="50%"
                                    class="pa-2"
                                >
                                    <a 
                                        href=""
                                        class="px-4 py-3"
                                    >
                                        <div
                                            class="d-flex align-center"
                                        >
                                            <v-icon
                                                color="white" 
                                                large
                                                class="mr-2"
                                            >
                                                mdi-apple
                                            </v-icon>
                                            <div>
                                                <p class="mb-1">Download via</p>
                                                <p class="mb-0"><strong>Apple Store</strong></p>
                                            </div>
                                        </div>
                                    </a>
                                </div>
                                <div
                                    width="50%"
                                    class="pa-2"
                                >
                                    <a 
                                        href=""
                                        class="px-4 py-3"
                                    >
                                        <div
                                            class="d-flex align-center"
                                        >
                                            <v-icon
                                                color="white" 
                                                large
                                                class="mr-2"
                                            >
                                                mdi-google-play
                                            </v-icon>
                                            <div>
                                                <p class="mb-1">Download via</p>
                                                <p class="mb-0"><strong>Google Play</strong></p>
                                            </div>
                                        </div>
                                    </a>
                                </div>
                            </div> -->
                        </div>
                    </v-col>
                </v-row>
            </div>
        </div>
        <div class="footer-credit">
            <div class="container--fluid">
                <div class="d-md-flex d-sm-flex-column align-center py-4">
                    <a 
                        href="" 
                        class="py-4"
                        width="132"
                        height="22"
                    >
                        <v-img
                            :src="logo" 
                            width="132"
                        ></v-img>
                    </a>
                    <v-spacer></v-spacer>
                    <p>Copyright &copy; {{year}} BDEvents - All rights reserved.</p>
                </div> 
            </div>
        </div>
    </footer>
</template>

<script>
    import footerLogo from '../assets/Images/Footer/footer-logo.png'
    export default {
        name: 'Footer', 
        data: ()=> ({
            year: (new Date()).getFullYear(),
            logo: footerLogo, 
            latestPosts: [
                {
                    id: 1,
                    title: 'Top 20 Event and Conference Countries', 
                    date: 'November 23, 2018',
                    url: require('../assets/Images/Footer/LatestPost/LatestPost1.png'),
                },
                {
                    id: 2,
                    title: 'Budgets for Business Events', 
                    date: 'November 23, 2018',
                    url: require('../assets/Images/Footer/LatestPost/LatestPost2.png'),
                },
                {
                    id: 3,
                    title: '5 Ideas for Fun Family Activities', 
                    date: 'November 23, 2018',
                    url: require('../assets/Images/Footer/LatestPost/LatestPost3.png'),
                },
            ],
        }), 
        methods:{
            async getBlog(blogId){
                localStorage.setItem("blogId", blogId); 
            }, 
        }
    }
</script>

<style lang="scss">
    .footer{
        background-color: #121219; 
        background-image: url('../assets/Images/Footer/footer-bg.jpg'); 
        background-size: cover;
        background-position: center;
        color: #fff;
        .footer-menu{
            .footer-menu-title{
                font-size: 1.35rem;
                font-weight: 700;
            }
            .footer-menu-content{
                a.social-icon-outline{
                    background: #fb0; 
                    border-radius: 50%;
                    width: 40px;
                    height: 40px;
                    display: flex;
                    justify-content: center;
                    align-items: center;
                    
                    .v-icon{
                        font-size: 1.077rem;
                        color: #fff !important;
                    }
                    &:hover{
                        background: #fff; 
                        .v-icon{
                            color: #fb0 !important;
                        } 
                    }
                }
                a.social-icon-outline{
                    &:hover{
                        color: #fb0 !important;
                    }
                }
                .footerLatestPosts{
                    .v-image{
                        &:hover{
                            cursor: pointer;
                        }
                    }
                    .v-list-item__title{
                        &:hover{
                            color: #fb0;
                            cursor: pointer;
                        }
                    }
                }
                .app-div{
                    a{
                        border: 1px solid rgba(255,255,255,.1);
                        .v-icon{
                            color: #fff;
                        }
                        &:hover{
                            background-color: #fb0 !important;
                            color: #fff !important; 
                        }
                    }
                }
            }
        }
        .footer-credit{
            border-top: 1px solid rgba(255,255,255,.1);
        }
    }    

</style>
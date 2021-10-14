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
                        <v-row>
                            <v-col
                                sm="12"
                                v-for="blog in filterBlogs"
                                :key="blog.id"
                            >
                                <v-card
                                    elevation="0"
                                >
                                    <v-img
                                        :src="blog.url"
                                        class= "rounded-lg"
                                        width="100%"
                                        height= "491px"
                                        style="cursor:pointer;"
                                    >
                                        <div
                                            class="d-flex align-end pa-7"
                                            style="width:100%; height: 100%;"
                                        >
                                            <NuxtLink :to="{path: 'Blogs/Category/'+(blog.category).charAt(0).toUpperCase()+(blog.category).slice(1) }">
                                                <v-btn
                                                    class="rounded-pill yellowish--text text-uppercase" 
                                                    color="white"
                                                    style="font-weight: 400; letter-spacing: 0.25px"
                                                >
                                                    {{blog.category}}
                                                </v-btn>
                                            </NuxtLink>
                                        </div>
                                    </v-img>
                                    <v-card-title
                                        class="px-0 pb-0 d-inline-block text-truncate"
                                        style="max-width: 100%"
                                        @click="geTBlog(blog.id)"
                                    >
                                        <NuxtLink :to="{path: '../../Blogs/Detail/'+(blog.title).split(' ').join('-') }">
                                            {{blog.title}}
                                        </NuxtLink>
                                    </v-card-title>
                                    <v-card-text
                                        class="px-0 pt-2 pb-4 gray--text darken-3 text-justify"
                                    >
                                        {{blog.description}}
                                    </v-card-text>
                                    <v-card-text
                                        class="px-0 pt-0 mb-3"
                                    >
                                        <div class="d-flex align-center justify-space-between align-center">
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
                                                        {{blog.date}}
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
                                                        mdi-calendar-blank-outline
                                                    </v-icon>
                                                    <span class="body-2">
                                                        {{blog.comment}} comment
                                                    </span>
                                                </div>
                                            </div>
                                            <NuxtLink :to="{path: '../../Blogs/Detail/'+(blog.title).split(' ').join('-') }">
                                                <v-btn
                                                    color="yellowish"
                                                    class="white--text rounded-pill px-8 py-6 btn-style"
                                                    Height="40px"
                                                    min-width="64px"
                                                    @click="geTBlog(blog.id)"
                                                >
                                                    Read More
                                                </v-btn>
                                            </NuxtLink>
                                        </div>
                                    </v-card-text>
                                </v-card>
                            </v-col>
                        </v-row>
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
    </div>
</template>

<script>
    import SidebarAdvertise from '../components/SidebarAdvertise.vue'
    export default {
        name: 'BlogCategory',
        data: () => ({
            blogs: [
                {
                    id: '1',
                    title: 'Top 20 Event and Conference Country',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has. Sed ad dicam platonem, mea eros illum elitr id, ei has similique constituto.', 
                    category: 'Lists',
                    catId: '1', 
                    date: 'November 23, 2018',
                    comment: '1', 
                    url: require('../assets/Images/Blog/blog1.png'),
                }, 
                {
                    id: '2',
                    title: 'Budgets for Business Events',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has. Sed ad dicam platonem, mea eros illum elitr id, ei has similique constituto.', 
                    category: 'News',
                    catId: '2', 
                    date: 'November 23, 2018',
                    comment: '0', 
                    url: require('../assets/Images/Blog/blog2.png'),
                }, 
                {
                    id: '3',
                    title: '5 Ideas for Fun Family Activities',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has. Sed ad dicam platonem, mea eros illum elitr id, ei has similique constituto.', 
                    category: 'Lists',
                    catId: '1', 
                    date: 'November 23, 2018',
                    comment: '0', 
                    url: require('../assets/Images/Blog/blog1.png'),
                }, 
                {
                    id: '4',
                    title: 'Best Event Ticket Deals',
                    
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has. Sed ad dicam platonem, mea eros illum elitr id, ei has similique constituto.', 
                    category: 'Events',
                    catId: '3', 
                    date: 'November 23, 2018',
                    comment: '1', 
                    url: require('../assets/Images/Blog/blog2.png'),
                }, 
                {
                    id: '5',
                    title: 'Video Equipments for Events',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has. Sed ad dicam platonem, mea eros illum elitr id, ei has similique constituto.', 
                    category: 'events',
                    catId: '3', 
                    date: 'November 23, 2018',
                    comment: '0', 
                    url: require('../assets/Images/Blog/blog1.png'),
                }, 
                {
                    id: '6',
                    title: 'Best Event Musics',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has. Sed ad dicam platonem, mea eros illum elitr id, ei has similique constituto.', 
                    category: 'culture',
                    catId: '4', 
                    date: 'November 23, 2018',
                    comment: '1', 
                    url: require('../assets/Images/Blog/blog2.png'),
                }, 
                {
                    id: '7',
                    title: 'Top 20 Event and Conference Countries 2 xdtcfyvg tcyvgubh',
                    description: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has. Sed ad dicam platonem, mea eros illum elitr id, ei has similique constituto.', 
                    category: 'Lists',
                    catId: '1', 
                    date: 'November 23, 2018',
                    comment: '1', 
                    url: require('../assets/Images/Blog/blog1.png'),
                }, 
            ],
            filterBlogs: [], 
        }), 
        methods: {
            async geTBlog(id){
                localStorage.setItem("blogId", id);
                console.log(localStorage); 
            },
        },
        mounted(){
            // console.log(this.$route.params.BlogCategory.toLowerCase());
            this.filterBlogs = (this.blogs).filter(x => x.category.toLowerCase() === this.$route.params.BlogCategory.toLowerCase()); 
            // console.log(this.filterBlogs)
        }
    }
</script>
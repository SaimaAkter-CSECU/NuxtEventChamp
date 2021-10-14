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
                                sm="6"
                                xs="12" 
                                v-for="blog in blogs"
                                :key="blog.id"
                            >
                                <v-card
                                    elevation="0"
                                >
                                    <v-img
                                        :src="blog.url"
                                        class="rounded-lg"
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
                                        <NuxtLink :to="{path: 'Blogs/Detail/'+(blog.title).split(' ').join('-') }">
                                            {{blog.title}}
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
                                                    mdi-chat-outline
                                                </v-icon>
                                                <span class="body-2">
                                                    {{blog.comment}} comment
                                                </span>
                                            </div>
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
        name: 'Blogs',
        data: () => ({
            blogs: [
                {
                    id: '1',
                    title: 'Top 20 Event and Conference Country',
                    category: 'lists',
                    catId: '1', 
                    date: 'November 23, 2018',
                    comment: '1', 
                    url: require('../assets/Images/Blog/blog1.png'),
                }, 
                {
                    id: '2',
                    title: 'Budgets for Business Events',
                    category: 'News',
                    catId: '2', 
                    date: 'November 23, 2018',
                    comment: '0', 
                    url: require('../assets/Images/Blog/blog2.png'),
                }, 
                {
                    id: '3',
                    title: '5 Ideas for Fun Family Activities',
                    category: 'Lists',
                    catId: '1', 
                    date: 'November 23, 2018',
                    comment: '0', 
                    url: require('../assets/Images/Blog/blog1.png'),
                }, 
                {
                    id: '4',
                    title: 'Best Event Ticket Deals',
                    category: 'events',
                    catId: '3', 
                    date: 'November 23, 2018',
                    comment: '1', 
                    url: require('../assets/Images/Blog/blog2.png'),
                }, 
                {
                    id: '5',
                    title: 'Video Equipments for Events',
                    category: 'Events',
                    catId: '3', 
                    date: 'November 23, 2018',
                    comment: '0', 
                    url: require('../assets/Images/Blog/blog1.png'),
                }, 
                {
                    id: '6',
                    title: 'Best Event Musics',
                    category: 'Culture',
                    catId: '4', 
                    date: 'November 23, 2018',
                    comment: '1', 
                    url: require('../assets/Images/Blog/blog2.png'),
                }, 
                {
                    id: '7',
                    title: 'Top 20 Event and Conference Countries 2 xdtcfyvg tcyvgubh',
                    category: 'Lists',
                    catId: '1', 
                    date: 'November 23, 2018',
                    comment: '1', 
                    url: require('../assets/Images/Blog/blog1.png'),
                }, 
            ],
        }),
        methods: {
            async geTBlog(id){
                localStorage.setItem("blogId", id);
                console.log(localStorage); 
            },
        },
    }
</script>
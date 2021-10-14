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
                        <!-- Blog Details -->
                        <div class="white pa-0 rounded-lg">
                            <div class="blog-details">
                            <v-img
                                :src="blog.img1"
                                height="650px"
                            ></v-img>
                            <div
                                class="pa-8"
                            >
                                <div 
                                    class="text-p font-weight-normal text-justify mb-7" 
                                    v-html="blog.description1"
                                    style="line-height: 1.7" 
                                >
                                </div>
                                <v-img
                                    :src="blog.img2"
                                    v-show="blog.img2"
                                    class="rounded-lg"
                                ></v-img>
                                <div 
                                    v-show="blog.description2"
                                    class="text-p font-weight-normal text-justify my-7" 
                                    v-html="blog.description2"
                                    style="line-height: 1.7" 
                                >
                                </div>
                                <div
                                    class="d-flex align-center flex-wrap my-9"
                                >
                                    <div 
                                        class="d-flex align-center mr-5"
                                    >
                                        <v-icon
                                            color="yellowish"
                                            class="mr-2"
                                        >
                                            mdi-folder-outline
                                        </v-icon>
                                        <span class="body-2">
                                            <NuxtLink :to="{path: '../../Blogs/Category/'+blog.category}">
                                                {{blog.category}}
                                            </NuxtLink>
                                        </span>
                                    </div>
                                    <div 
                                        class="d-flex align-center mr-5"
                                    >
                                        <v-icon
                                            color="yellowish"
                                            class="mr-2"
                                        >
                                            mdi-calendar-blank-outline
                                        </v-icon>
                                        <span class="body-2">
                                            {{blog.date}}
                                        </span>
                                    </div>
                                    <div 
                                        class="d-flex align-center mr-4"
                                    >
                                        <v-icon
                                            color="yellowish"
                                            class="mr-2"
                                        >
                                            mdi-chat-outline
                                        </v-icon>
                                        <span class="body-2">
                                            {{blog.comment}} comment
                                        </span>
                                    </div>
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
                                                    class="mr-2"
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
                        <!-- Author Details -->
                        <div class="author-details white rounded-lg my-8">
                            <div
                                class="py-7 pl-8 text-h6"
                                style="border-bottom: 1px solid #eaeaea"
                            >
                                About the Author
                            </div>
                            <div
                                class="pa-8"
                            >
                                <v-row
                                    class="align-center"
                                >
                                    <v-col
                                        col="12"
                                        sm="2"
                                        xs="12"
                                    >
                                        <v-img
                                            :src="blog.authorImg"
                                            class="rounded-lg"
                                            width="100%"
                                        ></v-img>
                                    </v-col>
                                    <v-col
                                        col="12"
                                        sm="10"
                                        xs="12"
                                    >
                                        <div
                                            class="author-title subtitle-1 mb-3"
                                        >
                                            {{blog.authorName}}
                                        </div>
                                        <div
                                            class="text-p mb-3"
                                        >
                                            {{blog.authorDetails}}
                                        </div>
                                        <div
                                            class="d-flex align-center"
                                        >
                                            <a 
                                                :href="blog.authorFacebook"
                                                class="mr-0"
                                            >
                                                <v-icon
                                                    class="author-social-icons"
                                                    large
                                                >
                                                    mdi-alpha-f
                                                </v-icon>
                                            </a>
                                            <a 
                                                :href="blog.authorInstagram"
                                                class="mr-2"
                                            >
                                                <v-icon
                                                    class="author-social-icons"
                                                >
                                                    mdi-instagram
                                                </v-icon>
                                            </a>
                                            <a 
                                                :href="blog.authorTwitter"
                                                class="mr-2"
                                            >
                                                <v-icon
                                                    class="author-social-icons"
                                                >
                                                    mdi-twitter
                                                </v-icon>
                                            </a>
                                            <a 
                                                :href="blog.authorYoutube"
                                                class="mr-2"
                                            >
                                                <v-icon
                                                    class="author-social-icons"
                                                >
                                                    mdi-youtube
                                                </v-icon>
                                            </a>
                                        </div>
                                    </v-col>
                                </v-row>
                            </div>
                        </div>
                        <!-- Related Blogs -->
                        <div class="white rounded-lg my-8">
                            <div
                                class="py-7 pl-8 text-h6"
                                style="border-bottom: 1px solid #eaeaea"
                            >
                                Related blogs
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
                        </div>
                        <!-- Display Comment -->
                        <div 
                            class="white rounded-lg my-8"
                            v-show="(blog.comment > 0)" 
                        >
                            <div
                                class="py-7 pl-8 text-h6"
                                style="border-bottom: 1px solid #eaeaea"
                            >
                                {{blog.comment}} Comment
                            </div>
                            <div
                                class="pa-8"
                            >
                                <v-row
                                    class="align-center"
                                    v-for="commentDetail in blog.commentDetails"
                                    :key="commentDetail.id"
                                >
                                    <v-col
                                        col="12"
                                        sm="2"
                                        xs="2"
                                    >
                                        <v-img
                                            :src="commentDetail.userImg"
                                            class="rounded-lg"
                                            width="100%"
                                        ></v-img>
                                    </v-col>
                                    <v-col
                                        col="12"
                                        sm="10"
                                        xs="10"
                                    >
                                        <div
                                            class="author-title subtitle-1 mb-3"
                                        >
                                            {{commentDetail.userName}}
                                        </div>
                                        <div
                                            class="text-p mb-3"
                                        >
                                            {{commentDetail.comment}}
                                        </div>
                                        <div
                                            class="d-flex align-center flex-wrap"
                                        >
                                            <div class="d-flex align-center mr-5">                                        
                                                <v-icon
                                                    class="gray--text mr-2"
                                                    small
                                                >
                                                    mdi-clock-time-four-outline
                                                </v-icon>
                                                <span
                                                    class="grey--text subtitle-2"
                                                >
                                                    {{commentDetail.date}}
                                                </span>
                                            </div>
                                            <div class="d-flex align-center">                                        
                                                <v-icon
                                                    class="grey--text mr-2"
                                                    small
                                                >
                                                    mdi-reply
                                                </v-icon>
                                                <span
                                                    class="grey--text subtitle-2"
                                                >
                                                    Reply
                                                </span>
                                            </div>
                                        </div>
                                    </v-col>
                                </v-row>
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
                    <SidebarAdvertise />
                </v-col>
            </v-row>
        </div>
    </div>
</template>

<script>
    import SidebarAdvertise from '../components/SidebarAdvertise.vue'
    export default {
        name: 'BlogDetail',
        data: () => ({
            blogs: [
                {
                    id: 1,
                    title: 'Top 20 Event and Conference Country',
                    description1: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has. Sed ad dicam platonem, mea eros illum elitr id, ei has similique constituto. Ea movet saperet rationibus sit, pri autem aliquip invidunt an. Consetetur omittantur consequuntur eos et. <strong> Eleifend praesent iudicabit no mea, tollit persequeris ex pri, tota splendide voluptaria in pri.</strong> Ad per tale aliquip, ei sit viris commune albucius. Eos aliquip scaevola ut, eum alii mentitum prodesset no, his ne suas atomorum. Et numquam deleniti ponderum vis, quod error at mei. Novum blandit adolescens sea te. Ea eum cetero scaevola.<br /><br />In his meis porro viris, illud imperdiet reprimique et vim. Feugiat atomorum reprehendunt vix ei, ei facete regione pri. Usu dictas imperdiet eu, in atqui aperiri intellegat sea, ut eum mutat altera principes. Te sit quaeque oportere, has modus inani ceteros ad. Impedit blandit deseruisse duo ea, ne graecis deleniti incorrupte usu. Ut mei splendide accommodare. An pri iisque meliore, eam ei splendide eloquentiam philosophia. <u>Ne per meis eleifend electram.</u> Ne eam porro aliquam invidunt. Minim docendi eloquentiam cum ad. Quo ea mazim ubique, ex est fuisset blandit scaevola. Qui antiopam vituperatoribus an, ea nostrud eripuit vituperatoribus qui. In eam diam nominati, per ea alia luptatum. <span class="yellowish--text">Nam habemus electram democritum ut.</span> Mei ea omnium admodum intellegat. Habeo atqui molestiae at mei, an nec ridens consequuntur. Quem nulla cum ei, his ipsum apeirian no, per at eius iriure aperiri. Sed dicam interesset ei. Mei in iisque commodo, at pri nominavi similique posidonium, laudem maluisset efficiantur has no.<br/><br /><br />His verterem consectetuer consequuntur ne, no virtute atomorum usu. <b> Eu quo nemore causae tacimates, eos viderer persequeris an.</b> Cu molestie consulatu qui. Natum labores perfecto no ius, pri dico mundi inciderint id. Ei usu dico libris postea. Cu graeco doctus splendide qui, ei eum probo regione.', 
                    description2: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has. Sed ad dicam platonem, mea eros illum elitr id, ei has similique constituto. Ea movet saperet rationibus sit, pri autem aliquip invidunt an. Consetetur omittantur consequuntur eos et. <strong> Eleifend praesent iudicabit no mea, tollit persequeris ex pri, tota splendide voluptaria in pri.</strong> Ad per tale aliquip, ei sit viris commune albucius. Eos aliquip scaevola ut, eum alii mentitum prodesset no, his ne suas atomorum. Et numquam deleniti ponderum vis, quod error at mei. Novum blandit adolescens sea te. Ea eum cetero scaevola.<br />In his meis porro viris, illud imperdiet reprimique et vim. Feugiat atomorum reprehendunt vix ei, ei facete regione pri. Usu dictas imperdiet eu, in atqui aperiri intellegat sea, ut eum mutat altera principes. Te sit quaeque oportere, has modus inani ceteros ad. Impedit blandit deseruisse duo ea, ne graecis deleniti incorrupte usu. Ut mei splendide accommodare. An pri iisque meliore, eam ei splendide eloquentiam philosophia. <u>Ne per meis eleifend electram.</u> Ne eam porro aliquam invidunt. Minim docendi eloquentiam cum ad. Quo ea mazim ubique, ex est fuisset blandit scaevola. Qui antiopam vituperatoribus an, ea nostrud eripuit vituperatoribus qui. In eam diam nominati, per ea alia luptatum. <span class="yellowish--text">Nam habemus electram democritum ut.</span> Mei ea omnium admodum intellegat. Habeo atqui molestiae at mei, an nec ridens consequuntur. Quem nulla cum ei, his ipsum apeirian no, per at eius iriure aperiri. Sed dicam interesset ei. Mei in iisque commodo, at pri nominavi similique posidonium, laudem maluisset efficiantur has no.<br/>His verterem consectetuer consequuntur ne, no virtute atomorum usu. <b> Eu quo nemore causae tacimates, eos viderer persequeris an.</b> Cu molestie consulatu qui. Natum labores perfecto no ius, pri dico mundi inciderint id. Ei usu dico libris postea. Cu graeco doctus splendide qui, ei eum probo regione.', 
                    category: 'Lists',
                    catId: 1, 
                    date: 'November 23, 2018',
                    comment: 1, 
                    img1: require('../assets/Images/Blog/blog1.png'),
                    img2: require('../assets/Images/Blog/blog2.png'),
                    authorName: 'VENESSA CASTLE.', 
                    authorDetails: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has', 
                    authorImg: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/avatar-150x150.jpg',
                    authorFacebook: 'https://www.facebook.com/', 
                    authorInstagram: 'https://www.instagram.com/', 
                    authorTwitter: 'https://twitter.com/', 
                    authorYoutube: 'https://www.youtube.com/', 
                    commentDetails:[
                        {
                            id: 1,
                            userName: 'John Doe', 
                            comment: 'His verterem consectetuer consequuntur ne, no virtute atomorum usu. Eu quo nemore causae tacimates, eos viderer persequeris an.',
                            date: 'Aprile 14, 2021', 
                            userImg: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/avatar-150x150.jpg'
                        }
                    ],
                }, 
                {
                    id: '2',
                    title: 'Budgets for Business Events',
                    description1: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has. Sed ad dicam platonem, mea eros illum elitr id, ei has similique constituto. Ea movet saperet rationibus sit, pri autem aliquip invidunt an. Consetetur omittantur consequuntur eos et. <strong> Eleifend praesent iudicabit no mea, tollit persequeris ex pri, tota splendide voluptaria in pri.</strong> Ad per tale aliquip, ei sit viris commune albucius. Eos aliquip scaevola ut, eum alii mentitum prodesset no, his ne suas atomorum. Et numquam deleniti ponderum vis, quod error at mei. Novum blandit adolescens sea te. Ea eum cetero scaevola.<br /><br />In his meis porro viris, illud imperdiet reprimique et vim. Feugiat atomorum reprehendunt vix ei, ei facete regione pri. Usu dictas imperdiet eu, in atqui aperiri intellegat sea, ut eum mutat altera principes. Te sit quaeque oportere, has modus inani ceteros ad. Impedit blandit deseruisse duo ea, ne graecis deleniti incorrupte usu. Ut mei splendide accommodare. An pri iisque meliore, eam ei splendide eloquentiam philosophia. <u>Ne per meis eleifend electram.</u> Ne eam porro aliquam invidunt. Minim docendi eloquentiam cum ad. Quo ea mazim ubique, ex est fuisset blandit scaevola. Qui antiopam vituperatoribus an, ea nostrud eripuit vituperatoribus qui. In eam diam nominati, per ea alia luptatum. <span class="yellowish--text">Nam habemus electram democritum ut.</span> Mei ea omnium admodum intellegat. Habeo atqui molestiae at mei, an nec ridens consequuntur. Quem nulla cum ei, his ipsum apeirian no, per at eius iriure aperiri. Sed dicam interesset ei. Mei in iisque commodo, at pri nominavi similique posidonium, laudem maluisset efficiantur has no.<br/><br /><br />His verterem consectetuer consequuntur ne, no virtute atomorum usu. <b> Eu quo nemore causae tacimates, eos viderer persequeris an.</b> Cu molestie consulatu qui. Natum labores perfecto no ius, pri dico mundi inciderint id. Ei usu dico libris postea. Cu graeco doctus splendide qui, ei eum probo regione.', 
                    description2: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has. Sed ad dicam platonem, mea eros illum elitr id, ei has similique constituto. Ea movet saperet rationibus sit, pri autem aliquip invidunt an. Consetetur omittantur consequuntur eos et. <strong> Eleifend praesent iudicabit no mea, tollit persequeris ex pri, tota splendide voluptaria in pri.</strong> Ad per tale aliquip, ei sit viris commune albucius. Eos aliquip scaevola ut, eum alii mentitum prodesset no, his ne suas atomorum. Et numquam deleniti ponderum vis, quod error at mei. Novum blandit adolescens sea te. Ea eum cetero scaevola.<br />In his meis porro viris, illud imperdiet reprimique et vim. Feugiat atomorum reprehendunt vix ei, ei facete regione pri. Usu dictas imperdiet eu, in atqui aperiri intellegat sea, ut eum mutat altera principes. Te sit quaeque oportere, has modus inani ceteros ad. Impedit blandit deseruisse duo ea, ne graecis deleniti incorrupte usu. Ut mei splendide accommodare. An pri iisque meliore, eam ei splendide eloquentiam philosophia. <u>Ne per meis eleifend electram.</u> Ne eam porro aliquam invidunt. Minim docendi eloquentiam cum ad. Quo ea mazim ubique, ex est fuisset blandit scaevola. Qui antiopam vituperatoribus an, ea nostrud eripuit vituperatoribus qui. In eam diam nominati, per ea alia luptatum. <span class="yellowish--text">Nam habemus electram democritum ut.</span> Mei ea omnium admodum intellegat. Habeo atqui molestiae at mei, an nec ridens consequuntur. Quem nulla cum ei, his ipsum apeirian no, per at eius iriure aperiri. Sed dicam interesset ei. Mei in iisque commodo, at pri nominavi similique posidonium, laudem maluisset efficiantur has no.<br/>His verterem consectetuer consequuntur ne, no virtute atomorum usu. <b> Eu quo nemore causae tacimates, eos viderer persequeris an.</b> Cu molestie consulatu qui. Natum labores perfecto no ius, pri dico mundi inciderint id. Ei usu dico libris postea. Cu graeco doctus splendide qui, ei eum probo regione.', 
                    category: 'News',
                    catId: '2', 
                    date: 'November 23, 2018',
                    comment: '0', 
                    img1: require('../assets/Images/Blog/blog2.png'),
                    img2: require('../assets/Images/Blog/blog1.png'),
                    authorName: 'VENESSA CASTLE.', 
                    authorDetails: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has', 
                    authorImg: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/avatar-150x150.jpg',
                    authorFacebook: 'https://www.facebook.com/', 
                    authorInstagram: 'https://www.instagram.com/', 
                    authorTwitter: 'https://twitter.com/', 
                    authorYoutube: 'https://www.youtube.com/', 
                    commentDetails: [], 
                }, 
                {
                    id: '3',
                    title: '5 Ideas for Fun Family Activities',
                    description1: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has. Sed ad dicam platonem, mea eros illum elitr id, ei has similique constituto. Ea movet saperet rationibus sit, pri autem aliquip invidunt an. Consetetur omittantur consequuntur eos et. <strong> Eleifend praesent iudicabit no mea, tollit persequeris ex pri, tota splendide voluptaria in pri.</strong> Ad per tale aliquip, ei sit viris commune albucius. Eos aliquip scaevola ut, eum alii mentitum prodesset no, his ne suas atomorum. Et numquam deleniti ponderum vis, quod error at mei. Novum blandit adolescens sea te. Ea eum cetero scaevola.<br /><br />In his meis porro viris, illud imperdiet reprimique et vim. Feugiat atomorum reprehendunt vix ei, ei facete regione pri. Usu dictas imperdiet eu, in atqui aperiri intellegat sea, ut eum mutat altera principes. Te sit quaeque oportere, has modus inani ceteros ad. Impedit blandit deseruisse duo ea, ne graecis deleniti incorrupte usu. Ut mei splendide accommodare. An pri iisque meliore, eam ei splendide eloquentiam philosophia. <u>Ne per meis eleifend electram.</u> Ne eam porro aliquam invidunt. Minim docendi eloquentiam cum ad. Quo ea mazim ubique, ex est fuisset blandit scaevola. Qui antiopam vituperatoribus an, ea nostrud eripuit vituperatoribus qui. In eam diam nominati, per ea alia luptatum. <span class="yellowish--text">Nam habemus electram democritum ut.</span> Mei ea omnium admodum intellegat. Habeo atqui molestiae at mei, an nec ridens consequuntur. Quem nulla cum ei, his ipsum apeirian no, per at eius iriure aperiri. Sed dicam interesset ei. Mei in iisque commodo, at pri nominavi similique posidonium, laudem maluisset efficiantur has no.<br/><br /><br />His verterem consectetuer consequuntur ne, no virtute atomorum usu. <b> Eu quo nemore causae tacimates, eos viderer persequeris an.</b> Cu molestie consulatu qui. Natum labores perfecto no ius, pri dico mundi inciderint id. Ei usu dico libris postea. Cu graeco doctus splendide qui, ei eum probo regione.', 
                    description2: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has. Sed ad dicam platonem, mea eros illum elitr id, ei has similique constituto. Ea movet saperet rationibus sit, pri autem aliquip invidunt an. Consetetur omittantur consequuntur eos et. <strong> Eleifend praesent iudicabit no mea, tollit persequeris ex pri, tota splendide voluptaria in pri.</strong> Ad per tale aliquip, ei sit viris commune albucius. Eos aliquip scaevola ut, eum alii mentitum prodesset no, his ne suas atomorum. Et numquam deleniti ponderum vis, quod error at mei. Novum blandit adolescens sea te. Ea eum cetero scaevola.<br />In his meis porro viris, illud imperdiet reprimique et vim. Feugiat atomorum reprehendunt vix ei, ei facete regione pri. Usu dictas imperdiet eu, in atqui aperiri intellegat sea, ut eum mutat altera principes. Te sit quaeque oportere, has modus inani ceteros ad. Impedit blandit deseruisse duo ea, ne graecis deleniti incorrupte usu. Ut mei splendide accommodare. An pri iisque meliore, eam ei splendide eloquentiam philosophia. <u>Ne per meis eleifend electram.</u> Ne eam porro aliquam invidunt. Minim docendi eloquentiam cum ad. Quo ea mazim ubique, ex est fuisset blandit scaevola. Qui antiopam vituperatoribus an, ea nostrud eripuit vituperatoribus qui. In eam diam nominati, per ea alia luptatum. <span class="yellowish--text">Nam habemus electram democritum ut.</span> Mei ea omnium admodum intellegat. Habeo atqui molestiae at mei, an nec ridens consequuntur. Quem nulla cum ei, his ipsum apeirian no, per at eius iriure aperiri. Sed dicam interesset ei. Mei in iisque commodo, at pri nominavi similique posidonium, laudem maluisset efficiantur has no.<br/>His verterem consectetuer consequuntur ne, no virtute atomorum usu. <b> Eu quo nemore causae tacimates, eos viderer persequeris an.</b> Cu molestie consulatu qui. Natum labores perfecto no ius, pri dico mundi inciderint id. Ei usu dico libris postea. Cu graeco doctus splendide qui, ei eum probo regione.', 
                    category: 'Lists',
                    catId: '1', 
                    date: 'November 23, 2018',
                    comment: '0', 
                    img1: require('../assets/Images/Blog/blog1.png'),
                    img2: require('../assets/Images/Blog/blog2.png'),
                    authorName: 'VENESSA CASTLE.', 
                    authorDetails: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has', 
                    authorImg: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/avatar-150x150.jpg',
                    authorFacebook: 'https://www.facebook.com/', 
                    authorInstagram: 'https://www.instagram.com/', 
                    authorTwitter: 'https://twitter.com/', 
                    authorYoutube: 'https://www.youtube.com/', 
                    commentDetails: [], 
                }, 
                {
                    id: '4',
                    title: 'Best Event Ticket Deals',
                    description1: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has. Sed ad dicam platonem, mea eros illum elitr id, ei has similique constituto. Ea movet saperet rationibus sit, pri autem aliquip invidunt an. Consetetur omittantur consequuntur eos et. <strong> Eleifend praesent iudicabit no mea, tollit persequeris ex pri, tota splendide voluptaria in pri.</strong> Ad per tale aliquip, ei sit viris commune albucius. Eos aliquip scaevola ut, eum alii mentitum prodesset no, his ne suas atomorum. Et numquam deleniti ponderum vis, quod error at mei. Novum blandit adolescens sea te. Ea eum cetero scaevola.<br /><br />In his meis porro viris, illud imperdiet reprimique et vim. Feugiat atomorum reprehendunt vix ei, ei facete regione pri. Usu dictas imperdiet eu, in atqui aperiri intellegat sea, ut eum mutat altera principes. Te sit quaeque oportere, has modus inani ceteros ad. Impedit blandit deseruisse duo ea, ne graecis deleniti incorrupte usu. Ut mei splendide accommodare. An pri iisque meliore, eam ei splendide eloquentiam philosophia. <u>Ne per meis eleifend electram.</u> Ne eam porro aliquam invidunt. Minim docendi eloquentiam cum ad. Quo ea mazim ubique, ex est fuisset blandit scaevola. Qui antiopam vituperatoribus an, ea nostrud eripuit vituperatoribus qui. In eam diam nominati, per ea alia luptatum. <span class="yellowish--text">Nam habemus electram democritum ut.</span> Mei ea omnium admodum intellegat. Habeo atqui molestiae at mei, an nec ridens consequuntur. Quem nulla cum ei, his ipsum apeirian no, per at eius iriure aperiri. Sed dicam interesset ei. Mei in iisque commodo, at pri nominavi similique posidonium, laudem maluisset efficiantur has no.<br/><br /><br />His verterem consectetuer consequuntur ne, no virtute atomorum usu. <b> Eu quo nemore causae tacimates, eos viderer persequeris an.</b> Cu molestie consulatu qui. Natum labores perfecto no ius, pri dico mundi inciderint id. Ei usu dico libris postea. Cu graeco doctus splendide qui, ei eum probo regione.', 
                    description2: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has. Sed ad dicam platonem, mea eros illum elitr id, ei has similique constituto. Ea movet saperet rationibus sit, pri autem aliquip invidunt an. Consetetur omittantur consequuntur eos et. <strong> Eleifend praesent iudicabit no mea, tollit persequeris ex pri, tota splendide voluptaria in pri.</strong> Ad per tale aliquip, ei sit viris commune albucius. Eos aliquip scaevola ut, eum alii mentitum prodesset no, his ne suas atomorum. Et numquam deleniti ponderum vis, quod error at mei. Novum blandit adolescens sea te. Ea eum cetero scaevola.<br />In his meis porro viris, illud imperdiet reprimique et vim. Feugiat atomorum reprehendunt vix ei, ei facete regione pri. Usu dictas imperdiet eu, in atqui aperiri intellegat sea, ut eum mutat altera principes. Te sit quaeque oportere, has modus inani ceteros ad. Impedit blandit deseruisse duo ea, ne graecis deleniti incorrupte usu. Ut mei splendide accommodare. An pri iisque meliore, eam ei splendide eloquentiam philosophia. <u>Ne per meis eleifend electram.</u> Ne eam porro aliquam invidunt. Minim docendi eloquentiam cum ad. Quo ea mazim ubique, ex est fuisset blandit scaevola. Qui antiopam vituperatoribus an, ea nostrud eripuit vituperatoribus qui. In eam diam nominati, per ea alia luptatum. <span class="yellowish--text">Nam habemus electram democritum ut.</span> Mei ea omnium admodum intellegat. Habeo atqui molestiae at mei, an nec ridens consequuntur. Quem nulla cum ei, his ipsum apeirian no, per at eius iriure aperiri. Sed dicam interesset ei. Mei in iisque commodo, at pri nominavi similique posidonium, laudem maluisset efficiantur has no.<br/>His verterem consectetuer consequuntur ne, no virtute atomorum usu. <b> Eu quo nemore causae tacimates, eos viderer persequeris an.</b> Cu molestie consulatu qui. Natum labores perfecto no ius, pri dico mundi inciderint id. Ei usu dico libris postea. Cu graeco doctus splendide qui, ei eum probo regione.', 
                    category: 'Events',
                    catId: '3', 
                    date: 'November 23, 2018',
                    comment: '1', 
                    img1: require('../assets/Images/Blog/blog2.png'),
                    img2: require('../assets/Images/Blog/blog1.png'),
                    authorName: 'VENESSA CASTLE.', 
                    authorDetails: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has', 
                    authorImg: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/avatar-150x150.jpg',
                    authorFacebook: 'https://www.facebook.com/', 
                    authorInstagram: 'https://www.instagram.com/', 
                    authorTwitter: 'https://twitter.com/', 
                    authorYoutube: 'https://www.youtube.com/', 
                    commentDetails:[
                        {
                            id: 1,
                            userName: 'John Doe', 
                            comment: 'His verterem consectetuer consequuntur ne, no virtute atomorum usu. Eu quo nemore causae tacimates, eos viderer persequeris an.',
                            date: 'Aprile 14, 2021', 
                            userImg: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/avatar-150x150.jpg'
                        }
                    ],
                }, 
                {
                    id: '5',
                    title: 'Video Equipments for Events',
                    description1: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has. Sed ad dicam platonem, mea eros illum elitr id, ei has similique constituto. Ea movet saperet rationibus sit, pri autem aliquip invidunt an. Consetetur omittantur consequuntur eos et. <strong> Eleifend praesent iudicabit no mea, tollit persequeris ex pri, tota splendide voluptaria in pri.</strong> Ad per tale aliquip, ei sit viris commune albucius. Eos aliquip scaevola ut, eum alii mentitum prodesset no, his ne suas atomorum. Et numquam deleniti ponderum vis, quod error at mei. Novum blandit adolescens sea te. Ea eum cetero scaevola.<br /><br />In his meis porro viris, illud imperdiet reprimique et vim. Feugiat atomorum reprehendunt vix ei, ei facete regione pri. Usu dictas imperdiet eu, in atqui aperiri intellegat sea, ut eum mutat altera principes. Te sit quaeque oportere, has modus inani ceteros ad. Impedit blandit deseruisse duo ea, ne graecis deleniti incorrupte usu. Ut mei splendide accommodare. An pri iisque meliore, eam ei splendide eloquentiam philosophia. <u>Ne per meis eleifend electram.</u> Ne eam porro aliquam invidunt. Minim docendi eloquentiam cum ad. Quo ea mazim ubique, ex est fuisset blandit scaevola. Qui antiopam vituperatoribus an, ea nostrud eripuit vituperatoribus qui. In eam diam nominati, per ea alia luptatum. <span class="yellowish--text">Nam habemus electram democritum ut.</span> Mei ea omnium admodum intellegat. Habeo atqui molestiae at mei, an nec ridens consequuntur. Quem nulla cum ei, his ipsum apeirian no, per at eius iriure aperiri. Sed dicam interesset ei. Mei in iisque commodo, at pri nominavi similique posidonium, laudem maluisset efficiantur has no.<br/><br /><br />His verterem consectetuer consequuntur ne, no virtute atomorum usu. <b> Eu quo nemore causae tacimates, eos viderer persequeris an.</b> Cu molestie consulatu qui. Natum labores perfecto no ius, pri dico mundi inciderint id. Ei usu dico libris postea. Cu graeco doctus splendide qui, ei eum probo regione.', 
                    description2: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has. Sed ad dicam platonem, mea eros illum elitr id, ei has similique constituto. Ea movet saperet rationibus sit, pri autem aliquip invidunt an. Consetetur omittantur consequuntur eos et. <strong> Eleifend praesent iudicabit no mea, tollit persequeris ex pri, tota splendide voluptaria in pri.</strong> Ad per tale aliquip, ei sit viris commune albucius. Eos aliquip scaevola ut, eum alii mentitum prodesset no, his ne suas atomorum. Et numquam deleniti ponderum vis, quod error at mei. Novum blandit adolescens sea te. Ea eum cetero scaevola.<br />In his meis porro viris, illud imperdiet reprimique et vim. Feugiat atomorum reprehendunt vix ei, ei facete regione pri. Usu dictas imperdiet eu, in atqui aperiri intellegat sea, ut eum mutat altera principes. Te sit quaeque oportere, has modus inani ceteros ad. Impedit blandit deseruisse duo ea, ne graecis deleniti incorrupte usu. Ut mei splendide accommodare. An pri iisque meliore, eam ei splendide eloquentiam philosophia. <u>Ne per meis eleifend electram.</u> Ne eam porro aliquam invidunt. Minim docendi eloquentiam cum ad. Quo ea mazim ubique, ex est fuisset blandit scaevola. Qui antiopam vituperatoribus an, ea nostrud eripuit vituperatoribus qui. In eam diam nominati, per ea alia luptatum. <span class="yellowish--text">Nam habemus electram democritum ut.</span> Mei ea omnium admodum intellegat. Habeo atqui molestiae at mei, an nec ridens consequuntur. Quem nulla cum ei, his ipsum apeirian no, per at eius iriure aperiri. Sed dicam interesset ei. Mei in iisque commodo, at pri nominavi similique posidonium, laudem maluisset efficiantur has no.<br/>His verterem consectetuer consequuntur ne, no virtute atomorum usu. <b> Eu quo nemore causae tacimates, eos viderer persequeris an.</b> Cu molestie consulatu qui. Natum labores perfecto no ius, pri dico mundi inciderint id. Ei usu dico libris postea. Cu graeco doctus splendide qui, ei eum probo regione.', 
                    category: 'events',
                    catId: '3', 
                    date: 'November 23, 2018',
                    comment: '0', 
                    img1: require('../assets/Images/Blog/blog1.png'),
                    img2: require('../assets/Images/Blog/blog2.png'),
                    authorName: 'VENESSA CASTLE.', 
                    authorDetails: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has', 
                    authorImg: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/avatar-150x150.jpg',
                    authorFacebook: 'https://www.facebook.com/', 
                    authorInstagram: 'https://www.instagram.com/', 
                    authorTwitter: 'https://twitter.com/', 
                    authorYoutube: 'https://www.youtube.com/', 
                    commentDetails: [], 
                }, 
                {
                    id: '6',
                    title: 'Best Event Musics',
                    description1: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has. Sed ad dicam platonem, mea eros illum elitr id, ei has similique constituto. Ea movet saperet rationibus sit, pri autem aliquip invidunt an. Consetetur omittantur consequuntur eos et. <strong> Eleifend praesent iudicabit no mea, tollit persequeris ex pri, tota splendide voluptaria in pri.</strong> Ad per tale aliquip, ei sit viris commune albucius. Eos aliquip scaevola ut, eum alii mentitum prodesset no, his ne suas atomorum. Et numquam deleniti ponderum vis, quod error at mei. Novum blandit adolescens sea te. Ea eum cetero scaevola.<br /><br />In his meis porro viris, illud imperdiet reprimique et vim. Feugiat atomorum reprehendunt vix ei, ei facete regione pri. Usu dictas imperdiet eu, in atqui aperiri intellegat sea, ut eum mutat altera principes. Te sit quaeque oportere, has modus inani ceteros ad. Impedit blandit deseruisse duo ea, ne graecis deleniti incorrupte usu. Ut mei splendide accommodare. An pri iisque meliore, eam ei splendide eloquentiam philosophia. <u>Ne per meis eleifend electram.</u> Ne eam porro aliquam invidunt. Minim docendi eloquentiam cum ad. Quo ea mazim ubique, ex est fuisset blandit scaevola. Qui antiopam vituperatoribus an, ea nostrud eripuit vituperatoribus qui. In eam diam nominati, per ea alia luptatum. <span class="yellowish--text">Nam habemus electram democritum ut.</span> Mei ea omnium admodum intellegat. Habeo atqui molestiae at mei, an nec ridens consequuntur. Quem nulla cum ei, his ipsum apeirian no, per at eius iriure aperiri. Sed dicam interesset ei. Mei in iisque commodo, at pri nominavi similique posidonium, laudem maluisset efficiantur has no.<br/><br /><br />His verterem consectetuer consequuntur ne, no virtute atomorum usu. <b> Eu quo nemore causae tacimates, eos viderer persequeris an.</b> Cu molestie consulatu qui. Natum labores perfecto no ius, pri dico mundi inciderint id. Ei usu dico libris postea. Cu graeco doctus splendide qui, ei eum probo regione.', 
                    description2: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has. Sed ad dicam platonem, mea eros illum elitr id, ei has similique constituto. Ea movet saperet rationibus sit, pri autem aliquip invidunt an. Consetetur omittantur consequuntur eos et. <strong> Eleifend praesent iudicabit no mea, tollit persequeris ex pri, tota splendide voluptaria in pri.</strong> Ad per tale aliquip, ei sit viris commune albucius. Eos aliquip scaevola ut, eum alii mentitum prodesset no, his ne suas atomorum. Et numquam deleniti ponderum vis, quod error at mei. Novum blandit adolescens sea te. Ea eum cetero scaevola.<br />In his meis porro viris, illud imperdiet reprimique et vim. Feugiat atomorum reprehendunt vix ei, ei facete regione pri. Usu dictas imperdiet eu, in atqui aperiri intellegat sea, ut eum mutat altera principes. Te sit quaeque oportere, has modus inani ceteros ad. Impedit blandit deseruisse duo ea, ne graecis deleniti incorrupte usu. Ut mei splendide accommodare. An pri iisque meliore, eam ei splendide eloquentiam philosophia. <u>Ne per meis eleifend electram.</u> Ne eam porro aliquam invidunt. Minim docendi eloquentiam cum ad. Quo ea mazim ubique, ex est fuisset blandit scaevola. Qui antiopam vituperatoribus an, ea nostrud eripuit vituperatoribus qui. In eam diam nominati, per ea alia luptatum. <span class="yellowish--text">Nam habemus electram democritum ut.</span> Mei ea omnium admodum intellegat. Habeo atqui molestiae at mei, an nec ridens consequuntur. Quem nulla cum ei, his ipsum apeirian no, per at eius iriure aperiri. Sed dicam interesset ei. Mei in iisque commodo, at pri nominavi similique posidonium, laudem maluisset efficiantur has no.<br/>His verterem consectetuer consequuntur ne, no virtute atomorum usu. <b> Eu quo nemore causae tacimates, eos viderer persequeris an.</b> Cu molestie consulatu qui. Natum labores perfecto no ius, pri dico mundi inciderint id. Ei usu dico libris postea. Cu graeco doctus splendide qui, ei eum probo regione.', 
                    category: 'culture',
                    catId: '4', 
                    date: 'November 23, 2018',
                    comment: '0', 
                    img1: require('../assets/Images/Blog/blog2.png'),
                    img2: require('../assets/Images/Blog/blog1.png'),
                    authorName: 'VENESSA CASTLE.', 
                    authorDetails: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has', 
                    authorImg: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/avatar-150x150.jpg',
                    authorFacebook: 'https://www.facebook.com/', 
                    authorInstagram: 'https://www.instagram.com/', 
                    authorTwitter: 'https://twitter.com/', 
                    authorYoutube: 'https://www.youtube.com/', 
                    commentDetails: [], 
                }, 
                {
                    id: '7',
                    title: 'Top 20 Event and Conference Countries 2 xdtcfyvg tcyvgubh',
                    description1: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has. Sed ad dicam platonem, mea eros illum elitr id, ei has similique constituto. Ea movet saperet rationibus sit, pri autem aliquip invidunt an. Consetetur omittantur consequuntur eos et. <strong> Eleifend praesent iudicabit no mea, tollit persequeris ex pri, tota splendide voluptaria in pri.</strong> Ad per tale aliquip, ei sit viris commune albucius. Eos aliquip scaevola ut, eum alii mentitum prodesset no, his ne suas atomorum. Et numquam deleniti ponderum vis, quod error at mei. Novum blandit adolescens sea te. Ea eum cetero scaevola.<br /><br />In his meis porro viris, illud imperdiet reprimique et vim. Feugiat atomorum reprehendunt vix ei, ei facete regione pri. Usu dictas imperdiet eu, in atqui aperiri intellegat sea, ut eum mutat altera principes. Te sit quaeque oportere, has modus inani ceteros ad. Impedit blandit deseruisse duo ea, ne graecis deleniti incorrupte usu. Ut mei splendide accommodare. An pri iisque meliore, eam ei splendide eloquentiam philosophia. <u>Ne per meis eleifend electram.</u> Ne eam porro aliquam invidunt. Minim docendi eloquentiam cum ad. Quo ea mazim ubique, ex est fuisset blandit scaevola. Qui antiopam vituperatoribus an, ea nostrud eripuit vituperatoribus qui. In eam diam nominati, per ea alia luptatum. <span class="yellowish--text">Nam habemus electram democritum ut.</span> Mei ea omnium admodum intellegat. Habeo atqui molestiae at mei, an nec ridens consequuntur. Quem nulla cum ei, his ipsum apeirian no, per at eius iriure aperiri. Sed dicam interesset ei. Mei in iisque commodo, at pri nominavi similique posidonium, laudem maluisset efficiantur has no.<br/><br /><br />His verterem consectetuer consequuntur ne, no virtute atomorum usu. <b> Eu quo nemore causae tacimates, eos viderer persequeris an.</b> Cu molestie consulatu qui. Natum labores perfecto no ius, pri dico mundi inciderint id. Ei usu dico libris postea. Cu graeco doctus splendide qui, ei eum probo regione.', 
                    description2: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has. Sed ad dicam platonem, mea eros illum elitr id, ei has similique constituto. Ea movet saperet rationibus sit, pri autem aliquip invidunt an. Consetetur omittantur consequuntur eos et. <strong> Eleifend praesent iudicabit no mea, tollit persequeris ex pri, tota splendide voluptaria in pri.</strong> Ad per tale aliquip, ei sit viris commune albucius. Eos aliquip scaevola ut, eum alii mentitum prodesset no, his ne suas atomorum. Et numquam deleniti ponderum vis, quod error at mei. Novum blandit adolescens sea te. Ea eum cetero scaevola.<br />In his meis porro viris, illud imperdiet reprimique et vim. Feugiat atomorum reprehendunt vix ei, ei facete regione pri. Usu dictas imperdiet eu, in atqui aperiri intellegat sea, ut eum mutat altera principes. Te sit quaeque oportere, has modus inani ceteros ad. Impedit blandit deseruisse duo ea, ne graecis deleniti incorrupte usu. Ut mei splendide accommodare. An pri iisque meliore, eam ei splendide eloquentiam philosophia. <u>Ne per meis eleifend electram.</u> Ne eam porro aliquam invidunt. Minim docendi eloquentiam cum ad. Quo ea mazim ubique, ex est fuisset blandit scaevola. Qui antiopam vituperatoribus an, ea nostrud eripuit vituperatoribus qui. In eam diam nominati, per ea alia luptatum. <span class="yellowish--text">Nam habemus electram democritum ut.</span> Mei ea omnium admodum intellegat. Habeo atqui molestiae at mei, an nec ridens consequuntur. Quem nulla cum ei, his ipsum apeirian no, per at eius iriure aperiri. Sed dicam interesset ei. Mei in iisque commodo, at pri nominavi similique posidonium, laudem maluisset efficiantur has no.<br/>His verterem consectetuer consequuntur ne, no virtute atomorum usu. <b> Eu quo nemore causae tacimates, eos viderer persequeris an.</b> Cu molestie consulatu qui. Natum labores perfecto no ius, pri dico mundi inciderint id. Ei usu dico libris postea. Cu graeco doctus splendide qui, ei eum probo regione.', 
                    category: 'Lists',
                    catId: '1', 
                    date: 'November 23, 2018',
                    comment: '0', 
                    img1: require('../assets/Images/Blog/blog1.png'),
                    img2: require('../assets/Images/Blog/blog2.png'),
                    authorName: 'VENESSA CASTLE.', 
                    authorDetails: 'Lorem ipsum dolor sit amet, voluptua iracundia disputationi an pri, his utinam principes dignissim ad. Ne nec dolore oblique nusquam, cu luptatum volutpat delicatissimi has', 
                    authorImg: 'https://demo.gloriathemes.com/eventchamp/demo/wp-content/uploads/2018/11/avatar-150x150.jpg',
                    authorFacebook: 'https://www.facebook.com/', 
                    authorInstagram: 'https://www.instagram.com/', 
                    authorTwitter: 'https://twitter.com/', 
                    authorYoutube: 'https://www.youtube.com/', 
                    commentDetails: [], 
                }, 
            ],
            blog: [], 
            relatedBlogs: [
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
            async geTBlog(id){
                localStorage.setItem("blogId", id);
                console.log(localStorage); 
            },
            async validate () {
                this.$refs.form.validate()
            },
        },
        mounted() {
            this.blog = this.blogs.find(x => x.id == localStorage.getItem('blogId') ); 
            console.log(this.blog);
            console.log(this.blog.commentDetails); 
        },
    }
</script>
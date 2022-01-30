<template>
    <div>
        <section 
            id="header"
            :style="(this.$nuxt.$route.path == '/') ? 'position:fixed; width:100%; z-index: 100;' : 'position:fixed; z-index:100;width:100%;' "
        >
            <v-toolbar
                :color="bgColor"
                :flat="this.elevation"
            >
                <div 
                    class="container--fluid d-flex justify-space-between align-center"
                    style="width:100%;"
                >
                    <v-toolbar-title>
                        <NuxtLink to="/">
                            <v-img
                                :src="logo"
                                height= "64px"
                                width= "200px"
                            >
                            </v-img>
                        </NuxtLink>
                    </v-toolbar-title>

                    <v-spacer></v-spacer>

                    <div class="d-lg-flex d-none justify-center align-center">
                        <div 
                            class="text-uppercase text-p menu-items"
                            v-bind:class="textColor"
                        >
                            <NuxtLink class="px-4 py-3" to="/">Home</NuxtLink>
                        </div>
                        <div 
                            class="text-uppercase text-p menu-items"
                            v-bind:class="textColor"
                        >
                            <NuxtLink class="px-4 py-3" to="/Events">Events</NuxtLink>
                        </div>
                        <div 
                            class="text-uppercase text-p menu-items"
                            v-bind:class="textColor"
                        >
                            <NuxtLink class="px-4 py-3" to="/Calendar">Calendar</NuxtLink>
                        </div>
                        <div 
                            class="text-uppercase text-p menu-items"
                            v-bind:class="textColor"
                        >
                            <NuxtLink class="px-4 py-3" to="/Speakers">Speakers</NuxtLink>
                        </div>
                        <div 
                            class="text-uppercase text-p menu-items"
                            v-bind:class="textColor"
                        >
                            <NuxtLink class="px-4 py-3" to="/Venues">Venues</NuxtLink>
                        </div>
                        <div 
                            class="text-uppercase text-p menu-items"
                            v-bind:class="textColor"
                        >
                            <NuxtLink class="px-4 py-3" to="/Blogs">Blogs</NuxtLink>
                        </div>
                        <div 
                            class="px-4 py-3 text-uppercase text-p menu-items"
                            v-bind:class="textColor"
                        >
                            <NuxtLink to="/Cart">
                                <v-icon
                                    :class="textColor"
                                >
                                    mdi-cart-outline
                                </v-icon>
                            </NuxtLink>
                        </div>
                        <div 
                            class="px-4 py-3 text-uppercase text-p menu-items"
                        >
                            <v-dialog
                                transition="dialog-top-transition"
                                max-width="400"
                                v-model="dialogLg"
                            >
                                <template v-slot:activator="{ on, attrs }">
                                    <v-btn
                                        :color="btnColor"
                                        class="white--text rounded-pill"
                                        v-bind="attrs"
                                        v-on="on"
                                        rounded-pill
                                        style="letter-spacing: 0px; font-weight: 400;"
                                        elevation="0"
                                    >
                                        <span v-show="loggedIn">My Profile</span>
                                        <span v-show="!loggedIn">Sign In</span>
                                    </v-btn>
                                </template>
                                <template >
                                    <v-card class="signInDialog">
                                        <v-toolbar
                                            color="white"
                                            light
                                            width="100%"
                                            elevation="1"
                                        >
                                            <span
                                                class="text-h6 font-weight-regular accent--text d-flex justify-center"
                                                style="width:100%;"
                                            >
                                                <span v-if="loggedIn">
                                                    <span>My Profile</span>
                                                </span>
                                                <span v-else>
                                                    <span v-if="SignInDialog">Sign In</span>
                                                    <span v-else>Sign Up</span>
                                                </span>
                                            </span>
                                            <!-- <span
                                                class="text-h6 font-weight-regular accent--text d-flex justify-center"
                                                style="width:100%;"
                                                v-if="SignInDialog"
                                            >
                                                Sign In
                                            </span>
                                            <span
                                                class="text-h6 font-weight-regular accent--text d-flex justify-center"
                                                style="width:100%;"
                                                v-else
                                            >
                                                Sign Up
                                            </span> -->

                                            <v-btn
                                                text
                                                @click="closeDialog()"
                                            >
                                                x
                                            </v-btn>
                                        </v-toolbar>
                                        <v-card-text class="pa-5 my-6">
                                            <div v-show="loggedIn">
                                                <div
                                                    class="w-100 d-flex justify-center"
                                                >
                                                    <v-icon
                                                        x-large
                                                        color="yellowish"
                                                        class="pa-2 rounded-circle userIcon"
                                                    >
                                                        mdi-account
                                                    </v-icon>
                                                </div>
                                                <v-list>
                                                    <v-list-item-group
                                                        v-model="group2"
                                                        color="yellowish"
                                                    >
                                                        <v-list-item
                                                            v-for="profileItem in profileItems"
                                                            :key="profileItem.id"
                                                            @click="closeDialog"
                                                        >
                                                            <NuxtLink 
                                                                :to="profileItem.path"
                                                                class="d-flex"
                                                            >
                                                                <v-list-item-icon>
                                                                    <v-icon>{{profileItem.icon}}</v-icon>
                                                                </v-list-item-icon>
                                                                <v-list-item-content>
                                                                    <v-list-item-title>{{profileItem.text}}</v-list-item-title>
                                                                </v-list-item-content>
                                                            </NuxtLink>
                                                        </v-list-item>
                                                    </v-list-item-group>
                                                </v-list>
                                            </div>
                                            
                                            <div v-show="!loggedIn">
                                                <div v-if="SignInDialog">
                                                    <v-form
                                                        ref="signInForm"
                                                        v-model="valid"
                                                        lazy-validation
                                                        class="mx-5"
                                                    >
                                                        <v-text-field
                                                            v-model="username"
                                                            :rules="inputRules"
                                                            label="Username"
                                                            outlined
                                                            required
                                                        ></v-text-field>

                                                        <v-text-field
                                                            v-model="password"
                                                            :type="showPass ? 'text' : 'password'"
                                                            :rules="inputRules"
                                                            label="Password"
                                                            :append-icon="showPass ? 'mdi-eye' : 'mdi-eye-off'"
                                                            outlined
                                                            required
                                                            @click:append="showPass = !showPass"
                                                        ></v-text-field>

                                                        <v-checkbox
                                                            v-model="checkbox"
                                                            label="Remember Me"
                                                            required
                                                        ></v-checkbox>

                                                        <v-btn
                                                            color="yellowish"
                                                            class="mr-4 white--text"
                                                            @click="SignIn"
                                                            large
                                                            block
                                                        >
                                                            Sign In
                                                        </v-btn>
                                                    </v-form>
                                                </div>
                                                <div v-else>
                                                    <v-form
                                                        ref="signUpForm"
                                                        v-model="valid"
                                                        lazy-validation
                                                        class="mx-5"
                                                    >
                                                        <v-text-field
                                                            v-model="registerUsername"
                                                            :rules="inputRules"
                                                            label="Username"
                                                            outlined
                                                            required
                                                        ></v-text-field>

                                                        <v-text-field
                                                            v-model="email"
                                                            :rules="emailRules"
                                                            label="Email" 
                                                            outlined
                                                            required
                                                        ></v-text-field>

                                                        <v-btn
                                                            color="yellowish"
                                                            class="mr-4 white--text"
                                                            @click="SignUp"
                                                            large
                                                            block
                                                        >
                                                            Sign Up
                                                        </v-btn>
                                                    </v-form>
                                                </div>
                                            </div>
                                        </v-card-text>
                                        <v-card-actions 
                                            class="justify-space-between pa-5"
                                            style="border-top: 1px solid #ececec"
                                        >
                                            <div 
                                                v-if="loggedIn"
                                                class="w-100"
                                            >
                                                <div
                                                    class="d-flex justify-center"
                                                >
                                                    <v-btn
                                                        class="btn-yellowish-style rounded-pill"
                                                        @click="logOut"
                                                        elevation="0"
                                                        large
                                                    >
                                                        Log Out
                                                    </v-btn>
                                                </div>
                                            </div>
                                            <div v-else>
                                                <v-subheader
                                                    class="text-uppercase"
                                                    v-if="SignInDialog"
                                                >
                                                    Lost Password? 
                                                </v-subheader>
                                                <v-subheader
                                                    class="text-uppercase blue-gray--text"
                                                    @click="SignInDialog = true"
                                                    v-else
                                                >
                                                    Sign In  
                                                </v-subheader> 

                                                <v-subheader
                                                    class="text-uppercase blue-gray--text"
                                                    v-if="SignInDialog"
                                                    @click="SignInDialog = false"
                                                >
                                                    Creat an account 
                                                </v-subheader> 
                                                
                                                <v-subheader
                                                    v-else
                                                    class="text-uppercase"
                                                    @click="closeDialog"
                                                >
                                                    Cancel
                                                </v-subheader>
                                            </div>
                                        </v-card-actions>
                                    </v-card>
                                </template>
                            </v-dialog>
                        </div>
                    </div>

                    <v-app-bar-nav-icon 
                        class="d-md-flex d-lg-none"
                        @click="drawer = true"
                    ></v-app-bar-nav-icon>

                </div>
            </v-toolbar>
        </section>

        <v-navigation-drawer
            v-model="drawer"
            absolute
            temporary
            style="z-index: 100; " 
        >
            <v-list
                nav
                dense
            >
                <v-list-item-group
                    v-model="group"
                    active-class="deep-purple--text text--accent-4"
                >
                    <v-list-item>
                        <v-list-item-icon>
                            <v-icon>mdi-home</v-icon>
                        </v-list-item-icon>
                        <v-list-item-title>
                            <NuxtLink to="/">Home</NuxtLink>
                        </v-list-item-title>
                    </v-list-item>

                    <v-list-item>
                        <v-list-item-icon>
                            <v-icon>mdi-view-grid-outline</v-icon>
                        </v-list-item-icon>
                        <v-list-item-title>
                            <NuxtLink to="/Events">Events</NuxtLink>
                        </v-list-item-title>
                    </v-list-item>

                    <v-list-item>
                        <v-list-item-icon>
                            <v-icon>mdi-calendar-blank-outline</v-icon>
                        </v-list-item-icon>
                        <v-list-item-title>
                            <NuxtLink to="/Calendar">Calendar</NuxtLink>
                        </v-list-item-title>
                    </v-list-item>

                    <v-list-item>
                        <v-list-item-icon>
                            <v-icon>mdi-account-supervisor-outline</v-icon>
                        </v-list-item-icon>
                        <v-list-item-title>
                            <NuxtLink to="/Speakers">Speakers</NuxtLink>
                        </v-list-item-title>
                    </v-list-item>

                    <v-list-item>
                        <v-list-item-icon>
                            <v-icon>mdi-map-legend</v-icon>
                        </v-list-item-icon>
                        <v-list-item-title>
                            <NuxtLink to="/Venues">Venues</NuxtLink>
                        </v-list-item-title>
                    </v-list-item>

                    <v-list-item>
                        <v-list-item-icon>
                            <v-icon>mdi-account</v-icon>
                        </v-list-item-icon>
                        <v-list-item-title>
                            <NuxtLink to="/Blogs">Blogs</NuxtLink>
                        </v-list-item-title>
                    </v-list-item>

                    <v-list-item>
                        <v-list-item-icon>
                            <v-icon>mdi-cart-outline</v-icon>
                        </v-list-item-icon>
                        <v-list-item-title>
                            <NuxtLink to="/Cart">Cart</NuxtLink>
                        </v-list-item-title>
                    </v-list-item>

                    <v-list-item>
                        <v-list-item-title>
                            <v-dialog
                                v-model="dialog"
                                transition="dialog-top-transition"
                                max-width="400"
                            >
                                <template v-slot:activator="{ on, attrs }">
                                    <v-btn
                                        :color="btnColor"
                                        class="white--text rounded-pill my-3"
                                        v-bind="attrs"
                                        v-on="on"
                                        rounded-pill
                                        block
                                        large
                                    >
                                        <span v-show="loggedIn">My Profile</span>
                                        <span v-show="!loggedIn">Sign In</span>
                                    </v-btn>
                                </template>
                                <template v-slot:default="dialog">
                                    <v-card class="signInDialog">
                                        <v-toolbar
                                            color="white"
                                            light
                                            width="100%"
                                            elevation="1"
                                        >
                                            <span
                                                class="text-h6 font-weight-regular accent--text d-flex justify-center"
                                                style="width:100%;"
                                            >
                                                <span v-if="loggedIn">
                                                    <span>My Profile</span>
                                                </span>
                                                <span v-if="!loggedIn">
                                                    <span v-if="SignInDialog">Sign In</span>
                                                    <span v-else>Sign Up</span>
                                                </span>
                                            </span>

                                            <v-btn
                                                text
                                                @click="dialog.value = false"
                                            >
                                                x
                                            </v-btn>
                                        </v-toolbar>
                                        <v-card-text class="pa-5 my-6">
                                            <div v-show="loggedIn">
                                                <v-list dense>
                                                    <v-list-item-group
                                                        color="primary"
                                                    >
                                                        <v-list-item
                                                            v-for="profileItem in profileItems"
                                                            :key="profileItem.id"
                                                        >
                                                            <NuxtLink 
                                                                :to="profileItem.path"
                                                                class="d-flex"
                                                            >
                                                                <v-list-item-icon>
                                                                    <v-icon>{{profileItem.icon}}</v-icon>
                                                                </v-list-item-icon>
                                                                <v-list-item-content>
                                                                    <v-list-item-title v-text="profileItem.text"></v-list-item-title>
                                                                </v-list-item-content>
                                                            </NuxtLink>
                                                        </v-list-item>
                                                    </v-list-item-group>
                                                </v-list>
                                            </div>
                                            
                                            <div v-show="!loggedIn">
                                                <div v-if="SignInDialog">
                                                    <v-form
                                                        ref="signInForm"
                                                        v-model="valid"
                                                        lazy-validation
                                                        class="mx-5"
                                                    >
                                                        <v-text-field
                                                            v-model="username"
                                                            :rules="inputRules"
                                                            label="Username"
                                                            outlined
                                                            required
                                                        ></v-text-field>

                                                        <v-text-field
                                                            v-model="password"
                                                            :type="showPass ? 'text' : 'password'"
                                                            :rules="inputRules"
                                                            label="Password"
                                                            :append-icon="showPass ? 'mdi-eye' : 'mdi-eye-off'"
                                                            outlined
                                                            required
                                                            @click:append="showPass = !showPass"
                                                        ></v-text-field>

                                                        <v-checkbox
                                                            v-model="checkbox"
                                                            label="Remember Me"
                                                            required
                                                        ></v-checkbox>

                                                        <v-btn
                                                            color="yellowish"
                                                            class="mr-4 white--text"
                                                            @click="SignIn"
                                                            large
                                                            block
                                                        >
                                                            Sign In
                                                        </v-btn>
                                                    </v-form>
                                                </div>
                                                <div v-else>
                                                    <v-form
                                                        ref="signInForm"
                                                        v-model="valid"
                                                        lazy-validation
                                                        class="mx-5"
                                                    >
                                                        <v-text-field
                                                            v-model="registerUsername"
                                                            :rules="inputRules"
                                                            label="Username"
                                                            outlined
                                                            required
                                                        ></v-text-field>

                                                        <v-text-field
                                                            v-model="email"
                                                            :rules="emailRules"
                                                            label="Email" 
                                                            outlined
                                                            required
                                                        ></v-text-field>

                                                        <v-btn
                                                            color="yellowish"
                                                            class="mr-4 white--text"
                                                            @click="SignUp"
                                                            large
                                                            block
                                                        >
                                                            Sign Up
                                                        </v-btn>
                                                    </v-form>
                                                </div>
                                            </div>
                                        </v-card-text>
                                        <v-card-actions 
                                            class="justify-space-between pa-5"
                                            style="border-top: 1px solid #ececec"
                                        >
                                            <div 
                                                v-if="loggedIn"
                                                class="w-100"
                                            >
                                                <div
                                                    class="d-flex justify-center"
                                                >
                                                    <v-btn
                                                        class="btn-yellowish-style rounded-pill"
                                                        @click="logOut"
                                                        elevation="0"
                                                        large
                                                    >
                                                        Log Out
                                                    </v-btn>
                                                </div>
                                            </div>
                                            <div v-else>
                                                <v-subheader
                                                    class="text-uppercase"
                                                    v-if="SignInDialog"
                                                >
                                                    Lost Password? 
                                                </v-subheader>
                                                <v-subheader
                                                    class="text-uppercase blue-gray--text"
                                                    @click="SignInDialog = true"
                                                    v-else
                                                >
                                                    Sign In  
                                                </v-subheader> 


                                                <v-subheader
                                                    class="text-uppercase blue-gray--text"
                                                    v-if="SignInDialog"
                                                    @click="SignInDialog = false"
                                                >
                                                    Creat an account 
                                                </v-subheader> 
                                                
                                                <v-subheader
                                                    v-else
                                                    class="text-uppercase"
                                                    @click="dialog.value = false"
                                                >
                                                    Cancel
                                                </v-subheader>
                                            </div>
                                        </v-card-actions>
                                    </v-card>
                                </template>
                            </v-dialog> 
                        </v-list-item-title>
                    </v-list-item>
                </v-list-item-group>
            </v-list>
        </v-navigation-drawer>

        <v-snackbar
            v-model="loginSnackbar"
            timeout="2000"
            color="primary"
        >
            {{loginSnackbarText}}

            <template v-slot:action="{ attrs }">
                <v-btn
                    color="white"
                    text
                    v-bind="attrs"
                    @click="loginSnackbar = false" 
                >
                Close
                </v-btn>
            </template>
        </v-snackbar>
    </div>
</template>

<script>
    import logo from "../assets/Images/logo.png";
    export default {
        name: 'Header',
        data: () => ({
            logo: logo, 
            bgColor : 'transparent', 
            textColor: 'white--text', 
            btnColor: 'yellowish', 
            elevation : false, 
            valid: true, 
            SignInDialog : true, 
            dialog: false,
            dialogLg: false,
            showPass: false, 
            password: '',
            username: '',
            registerUsername: '',
            email: '', 
            checkbox: false,
            inputRules: [
                v => !!v || 'This Field is required',
            ],
            emailRules: [
                v => !!v || 'E-mail is required',
                v => /.+@.+\..+/.test(v) || 'E-mail must be valid',

            ],
            drawer: false, 
            group: null, 
            group2: null, 
            users:[
                {
                    id: 1,
                    username: 'Saima',
                    password: 'Saima', 
                },
                {
                    id: 2,
                    username: 'Sovon',
                    password: 'Sovon', 
                },
            ],
            loginSnackbar: false,
            loginSnackbarText: '', 
            loggedIn: false,  
            profileItems: [
                {
                    id: 1,
                    text: 'My Events',
                    icon: 'mdi-view-grid-outline',
                    path: '/Profile/MyEvents', 
                },
                {
                    id: 2, 
                    text: 'My Blogs',
                    icon: 'mdi-account-outline',
                    path: '/Profile/MyBlogs', 
                },
                {
                    id: 3, 
                    text: 'Post an Event',
                    icon: 'mdi-account-outline',
                    path: '/Profile/Post-Event', 
                },
                {
                    id: 4, 
                    text: 'Post a Blog',
                    icon: 'mdi-account-details-outline',
                    path: '/Profile/Post-Blog', 
                },
            ],
        }),
        mounted() {
            window.onscroll = () => {
                this.changeColor();
            };
            this.changeColor(); 

            let userLoggedIn = localStorage.getItem('loggedIn'); 
            if(userLoggedIn){
                this.loggedIn = true;
            }
            else{
                this.loggedIn = false; 
            }
        },
        methods: {
            async changeColor() {
                if(this.$nuxt.$route.path == '/' || this.$nuxt.$route.path == ''){
                    if (document.body.scrollTop > 120 || document.documentElement.scrollTop > 120) {
                        this.bgColor = 'white';
                        this.textColor= "accent--text"; 
                        this.btnColor = "primary";
                        this.elevation = false;
                    }
                    else {
                        this.bgColor = 'transparent';
                        this.btnColor = "yellowish";
                        this.textColor= "white--text"; 
                        this.elevation = true;
                    }
                }
                else{
                    this.bgColor = 'white';
                    this.textColor= "accent--text"; 
                    this.btnColor = "primary";
                    this.elevation = false;
                }
            },
            async SignIn(){
                if(this.$refs.signInForm.validate()){
                    let user = this.users.find(x=> x.username == this.username && x.password == this.password);
                    // console.log(user)
                    if(user){
                        this.dialog = false; 
                        this.dialogLg = false; 
                        this.loginSnackbarText = 'Login Successfully!'; 
                        this.loginSnackbar = true; 
                        localStorage.setItem("loggedIn", 'true'); 
                        this.loggedIn= true; 
                        this.SignInDialog = false; 
                        // console.log(localStorage.getItem("loggedIn")); 
                    }
                    else{
                        this.loginSnackbarText = 'Credential Error!'; 
                        this.loginSnackbar = true; 
                    }
                }
            },
            async SignUp(){
                if(this.$refs.signUpForm.validate()){
                    this.dialog = false; 
                    this.loginSnackbarText = 'Sign Up Successfully!!!'; 
                    this.loginSnackbar = true; 
                }
            }, 
            async logOut(){
                localStorage.setItem("loggedIn", 'false'); 
                this.loggedIn = false;
                this.SignInDialog = true; 
                if(this.$route.path == "/Profile/MyEvents" || this.$route.path == "/Profile/MyBlogs"){
                    this.$router.push('/'); 
                }
            },
            async closeDialog(){
                this.dialogLg = false;
            }
        },
        
    }
</script>
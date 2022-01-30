<template>
    <div 
        class="subPageBanner"
        style="margin-top: 64px;"
    >
        <v-img
            :src="SubPageBanner"
            width="100%"
            height= "285px"
        >
            <v-overlay
                width="100%"
                height="100%"
                absolute
            >
                <div 
                    class="container--fluid white--text align-center"
                >
                    <div class="text-h2 font-weight-regular">
                        <span v-show="items.length == 2">
                            {{(this.$route.path).substring((this.$route.path).lastIndexOf('/') + 1)}}
                        </span>
                        <span v-show="items.length == 3">
                            {{
                                ((this.$route.path).substring((this.$route.path).lastIndexOf('/') + 1)).split('-').join(' ')
                            }}
                        </span>
                    </div>
                    <div class="mt-3">
                        <span class="subtitle-2 backToHome mr-2">
                            <NuxtLink to="/">Home</NuxtLink>
                        </span>
                        <span class="mr-2"> > </span>
                        <span
                            v-show="items.length == 2"
                        >
                            <span
                                color="yellowish"
                                class="yellowish--text subtitle-2"
                                style= "border-bottom: 2px solid #fb0"
                            >
                                {{(this.$route.path).substring((this.$route.path).lastIndexOf('/') + 1)}}
                            </span> 
                        </span>
                        <span
                            v-show="items.length == 3"
                        >
                            <span
                                class="white--text subtitle-2"
                            >
                                <NuxtLink :to="{path: '/'+secondItem.path}">
                                    {{secondItem.title}}
                                </NuxtLink>
                            </span>
                            <span class="mr-2"> > </span>
                            <span
                                color="yellowish"
                                class="yellowish--text subtitle-2"
                                style= "border-bottom: 2px solid #fb0"
                            >
                                {{thirdItem.title}}
                            </span> 
                        </span>
                    </div>
                </div>
            </v-overlay>
        </v-img>
    </div>
</template>

<script>
    import SubPageBanner from '../assets/Images/SubPageBanner.jpg' 
    export default {
        name: 'SubPageBanner',
        data: () => ({
            SubPageBanner: SubPageBanner, 
            title: '', 
            items: [
                {
                    id: 1, 
                    title: 'Home', 
                    path: '/',
                },
            ],
            item: '',
            secondItem: {},
            thirdItem: {},
        }),
        mounted() {
            console.log("banner path", this.$route.path);  
            // console.log("banner ", Object.keys(this.$route.params).length) 

            if(Object.keys(this.$route.params).length > 0) { 
                console.log("why here")
                if(this.$route.params.id){
                    this.item = this.$route.path.split('/')[1]; 
                    this.secondItem = {
                        id: 2,
                        title : this.item, 
                        path : this.item,
                    };
                    this.thirdItem = {
                        id: 3,
                        title : (this.$route.params.id).split('-').join(' '), 
                        path : '',
                    };
                    console.log(this.secondItem)
                    this.items.push(this.secondItem);
                    this.items.push(this.thirdItem);
                }

                else if(this.$route.params.EventCategory){
                    this.title = this.$route.params.EventCategory;
                    this.secondItem = {
                        id: 2,
                        title: 'Events',
                        path: 'Events'
                    };
                    this.thirdItem = {
                        id: 3,
                        title: (this.$route.path).substring((this.$route.path).lastIndexOf('/') + 1),
                        path: '', 
                    }
                    this.items.push(this.secondItem);
                    this.items.push(this.thirdItem);
                }
                else if(this.$route.params.BlogCategory){
                    this.secondItem = {
                        id: 2,
                        title: 'Blogs',
                        path: 'Blogs'
                    };
                    this.thirdItem = {
                        id: 3,
                        title: (this.$route.path).substring((this.$route.path).lastIndexOf('/') + 1),
                        path: '', 
                    }
                    this.items.push(this.secondItem);
                    this.items.push(this.thirdItem);
                }
                else if(this.$route.params.Location){
                    this.secondItem = {
                        id: 2,
                        title: 'Blogs',
                        path: 'Blogs'
                    };
                    this.thirdItem = {
                        id: 3,
                        title: (this.$route.path).substring((this.$route.path).lastIndexOf('/') + 1),
                        path: '', 
                    }
                    this.items.push(this.secondItem);
                    this.items.push(this.thirdItem);
                }
            }
            else{
                this.secondItem = {
                    id: 2,
                    title : (this.$route.path).substring((this.$route.path).lastIndexOf('/') + 1), 
                    path : '/'+(this.$route.path).substring((this.$route.path).lastIndexOf('/') + 1),
                };
                // console.log(this.items);
                this.items.push(this.secondItem);
                // console.log(this.items); 
            }
        },
    }
</script>
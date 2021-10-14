<template>
    <div
        class="white advertise-div rounded-lg mt-9"
    >
        <div
            class="py-7 px-9 text-h6"
            style="border-bottom: 1px solid #eaeaea"
        >
            Sponsors
        </div>
        <div
            class="pa-8 pt-3"
        >
            <v-row>
                <v-col
                    col="12"
                    sm="6"
                    xs="12"
                    v-for="sponsor in sponsorList"
                    :key="sponsor.id"
                >
                    <div
                        class="rounded-lg"
                        style="border: 1px solid #eaeaea"
                    >
                        <a :href="sponsor.link">
                            <v-img
                                :src="sponsor.img"
                                class="rounded-lg"
                                width="100%"
                                height="100%"
                            ></v-img>
                        </a> 
                    </div>
                </v-col>
            </v-row>
            
        </div>
        
    </div>
</template>

<script>
    
    export default {
        name: 'SidebarEventSponsor',
        props: ['event'], 
        data: () => ({
            sponsorList: [],
            
        }),
        mounted() {
            console.log(this.event[0].sponsors); 
            this.sponsorList = this.event[0].sponsors; 
            
        },
    }
</script>
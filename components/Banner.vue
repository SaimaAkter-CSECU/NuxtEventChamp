<template>
    <section 
      id="banner"
      style="height: 100vh;"
    >
        <div v-swiper="swiperOption" class="w-100 mx-auto relative">
            <div class="swiper-wrapper">
                <div
                  class="swiper-slide"
                  :key="bannerEvent.id"
                  v-for="bannerEvent in bannerEvents" 
                >
                <v-card 
                  class="slider-card-div"
                  style="max-height: 100vh; background-color: grey"
                >
                    <v-img
                      :src="bannerEvent.url"
                      style="cursor: pointer; height: 100vh"
                    >
                      <v-overlay
                        style="position: absolute; top:0; left: 0; right: 0; bottom: 0; cursor: default;"
                      >
                        <div class="d-flex flex-column justify-center align-center">
                          <NuxtLink :to="{path: 'Events/Category/'+(bannerEvent.category).charAt(0).toUpperCase()+(bannerEvent.category).slice(1) }">
                            <v-btn
                              color="yellowish" 
                              class="white--text mb-5 rounded-pill px-5 " 
                            >
                              {{bannerEvent.category}} 
                            </v-btn> 
                          </NuxtLink>
                          <div 
                            class="text-md-h2 text-sm-h4 font-weight-bold py-9"
                            style="font-family: Poppins !important;"
                          >
                            {{ bannerEvent.title }}
                          </div>
                          <div
                            class="d-flex justify-center align-center"
                          >
                            <span
                              class="pa-4 text-uppercase"
                            >
                              <v-icon
                                color="yellowish"
                                class="mr-3"
                              >
                                mdi-calendar-blank-outline
                              </v-icon>
                              <span>
                                {{ bannerEvent.date }}
                              </span>
                            </span>
                            <span
                              class="pa-4 text-uppercase"
                            >
                              <v-icon
                                color="yellowish"
                                class="mr-3"
                              >
                                mdi-map-marker-outline
                              </v-icon>
                              <span
                              >
                                <NuxtLink :to="{path: 'Venues/Location/'+(bannerEvent.location).charAt(0).toUpperCase()+(bannerEvent.location).slice(1) }">
                                  {{ bannerEvent.location }}
                                </NuxtLink>
                              </span>
                            </span>
                            <span
                              class="pa-4 text-uppercase"
                            >
                              <v-icon
                                color="yellowish"
                                class="mr-3"
                              >
                                mdi-map-legend
                              </v-icon>
                              <span
                                style="cursor:pointer;"
                                @click="getVenue(bannerEvent.venueId)"
                              >
                                <NuxtLink :to="{path: 'Venues/Detail/'+(bannerEvent.venue).split(' ').join('-') }">
                                  {{ bannerEvent.venue }}
                                </NuxtLink>
                              </span>
                            </span>
                          </div>
                            <div
                              class="pt-9 d-flex justify-center align-center banner-btn"
                            >
                              <v-btn
                                class="py-3 px-5 mx-2 white--text text-uppercase rounded-pill"
                                @click="getEvent(bannerEvent.id)"
                              >
                                <NuxtLink :to="{path: 'Events/Detail/'+(bannerEvent.title).split(' ').join('-') }">
                                  Details
                                </NuxtLink>
                              </v-btn>
                              <NuxtLink :to="{path: 'Events/Detail/'+(bannerEvent.title).split(' ').join('-') }">
                                <v-btn
                                  v-show="!(bannerEvent.cost == 'Free')"
                                  class="py-3 px-5 mx-2 white--text text-uppercase rounded-pill"
                                  @click="getEvent(bannerEvent.id)"
                                >
                                  Buy ticket
                                </v-btn>
                              </NuxtLink>
                            </div>
                        </div>
                      </v-overlay>
                    </v-img>
                </v-card>
                </div>
                
            </div>
            <div class="swiper-pagination" ></div>
        </div>
    </section>
</template>

<script>
  export default {
    name: "Banner",
    data: () => ({
      bannerEvents: [
        {
          id: 1,
          title: "Table Mountain Cableway",
          date: "April 14, 2022",
          location: "CapeTown",
          venueId: "2",
          venue: "Table Mountain",
          catId: 12,
          category: "Travel",
          cost: '150', 
          url: require("../assets/Images/Banner/banner1.png"),
        },
        {
          id: 2,
          title: "CA After Party",
          date: "February 14, 2022",
          location: "NewYork",
          venueId: "3",
          venue: "Victory Club",
          catId: 9,
          category: "Nightlife",
          cost: 'Free', 
          url: require("../assets/Images/Banner/banner2.png"),
        },
        {
          id: 3,
          title: "Eventchamp Conference",
          date: "March 12, 2021",
          location: "London",
          venueId: "5",
          venue: "London Arena",
          catId: 2,
          category: "Business",
          cost: '4500', 
          url: require("../assets/Images/Banner/banner3.png"),
        },
      ],
      swiperOption: {
        slidesPerView: 1,
        allowTouchMove: false,
        loop: false,
        // autoplay: {
        //   delay: 5000
        // },
        // navigation: false, 
        pagination: {
          el: ".swiper-pagination",
          clickable: true,
        },
      },
    }),
    methods: {
      async getEvent(id){
          localStorage.setItem("eventId", id);
      },
      async getVenue(venueId){
          localStorage.setItem("venueId", venueId);
      },
    },
  };
</script>


<template>
    <section id="banner">
        <div v-swiper="swiperOption" class="w-100 mx-auto relative">
            <div class="swiper-wrapper">
                <div
                  class="swiper-slide"
                  :key="bannerEvent.id"
                  v-for="bannerEvent in bannerEvents"
                >
                <v-card class="slider-card-div">
                    <v-img
                    :src="bannerEvent.url"
                    style="cursor: pointer; max-height: 100vh"
                    >
                      <v-overlay
                        style="position: absolute; top:0; left: 0; right: 0; bottom: 0; cursor: default;"
                      >
                        <div class="d-flex flex-column justify-center align-center">
                            <v-btn
                              color="yellowish" 
                              class="white--text mb-5 rounded-pill px-5 py-2" 
                              height="50"
                              min-width="110"
                            >
                              {{bannerEvent.category}}
                            </v-btn>
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
                                <span>
                                  {{ bannerEvent.location }}
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
                                  @click="goToVenue(bannerEvent.venueId)"
                                >
                                  {{ bannerEvent.venue }}
                                </span>
                              </span>
                            </div>
                            <div
                              class="pt-9 d-flex justify-center align-center banner-btn"
                            >
                              <v-btn
                                class="py-3 px-5 mx-2 white--text text-uppercase rounded-pill"
                                @click="goToEvent(bannerEvent.id)"
                              >
                                Details
                              </v-btn>
                              <v-btn
                                v-show="!(bannerEvent.cost == 'Free')"
                                class="py-3 px-5 mx-2 white--text text-uppercase rounded-pill"
                                @click="goToEvent(bannerEvent.id)"
                              >
                                Buy ticket
                              </v-btn>
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
          location: "Cape Town",
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
          location: "New York",
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
        loop: true,
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
      goToEvent(i){
        console.log(i);
      },
      goToVenue(x){
        console.log(x);
      }
    },
  };
</script>


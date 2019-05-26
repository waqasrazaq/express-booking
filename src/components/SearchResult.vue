<template>
    <v-card v-if="isDataAvailable()">
            <v-card-title class="grey lighten-4 py-4 title">
                Search Results
            </v-card-title>

            <v-container   class="pa-4">
                <v-layout row wrap>

                    <v-flex xs12>
                        <v-card color="blue" class="white--text">
                            <v-layout>
                                <v-flex xs5>
                                    <v-img
                                            :src="searchData.hotel_details.photos[0]['url']"
                                            height="300px"
                                            cover
                                    ></v-img>
                                </v-flex>
                                <v-flex xs7>
                                    <v-card-title primary-title>
                                        <div class="white--text">
                                            <div class="headline" >{{searchData.hotel_details.name}}</div>
                                            <div ><v-icon class="white--text">phone</v-icon> {{searchData.hotel_details.phone}}</div>
                                            <div ><v-icon class="white--text">location_on</v-icon>{{searchData.hotel_details.address1}}, {{searchData.hotel_details.address2}}, {{searchData.hotel_details.city}}, {{searchData.hotel_details.state}} </div>
                                            <div ><a class="white--text" :href="searchData.terms_and_conditions_url" target="_blank">Terms and Conditions</a></div>

                                        </div>
                                    </v-card-title>
                                </v-flex>
                            </v-layout>
                            <v-divider light></v-divider>
                            <v-card-actions class="pa-3">
                                Rate this album
                                <v-spacer></v-spacer>
                                <v-icon>star_border</v-icon>
                                <v-icon>star_border</v-icon>
                                <v-icon>star_border</v-icon>
                                <v-icon>star_border</v-icon>
                                <v-icon>star_border</v-icon>
                            </v-card-actions>
                        </v-card>
                    </v-flex>

                <!--<v-flex xs12 sm6 offset-sm3>
                    <v-card>
                        <v-img
                                :src="searchData.hotel_details.photos[0]['url']"
                                height="200px"
                        >
                        </v-img>

                        <v-card-title primary-title>
                            <div>
                                <div class="headline">{{searchData.hotel_details.name}}</div>
                                <div class="grey--text">Phone: {{searchData.hotel_details.phone}}</div>
                                <span class="grey--text">{{searchData.hotel_details.address1}}, {{searchData.hotel_details.address2}}, {{searchData.hotel_details.city}}, {{searchData.hotel_details.state}} </span>
                            </div>
                        </v-card-title>

                        <v-card-actions>
                            <v-btn flat>Share</v-btn>
                            <v-btn flat color="purple">Explore</v-btn>
                            <v-spacer></v-spacer>
                            <v-btn icon @click="show = !show">
                                <v-icon>{{ show ? 'keyboard_arrow_down' : 'keyboard_arrow_up' }}</v-icon>
                            </v-btn>
                        </v-card-actions>

                        <v-slide-y-transition>
                            <v-card-text v-show="show">
                                I'm a thing. But, like most politicians, he promised more than he could deliver. You won't have time for sleeping, soldier, not with all the bed making you'll be doing. Then we'll go with that data file! Hey, you add a one and two zeros to that or we walk! You're going to do his laundry? I've got to find a way to escape.
                            </v-card-text>
                        </v-slide-y-transition>
                    </v-card>
                </v-flex>-->
            </v-layout>


            </v-container>
    </v-card>
</template>

<script>
  export default {
    name: 'Hotel',
    props: ['searchData'],
    data: () => ({
    }),
    methods: {
      isDataAvailable () {
        return (this.searchData !== '');
      }
    }
  }
</script>

<style scoped>

</style>

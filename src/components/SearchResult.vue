<template>
    <v-card v-if="isDataAvailable()">
        <v-card-title class="grey lighten-3 py-3 title">
            Search results
        </v-card-title>

        <v-container class="pa-4">
            <v-layout row wrap>
                <v-flex xs12>
                    <v-card>
                        <v-layout>
                            <v-flex xs5>
                                <v-img
                                        :src="searchData.hotel_details.photos[0]['url']"
                                        height="250px"
                                        cover
                                ></v-img>
                            </v-flex>
                            <v-flex xs7>
                                <v-card-title primary-title>
                                    <div>
                                        <div class="headline pb-3">{{searchData.hotel_details.name}}</div>
                                        <div>
                                            <v-icon class="">phone</v-icon>
                                            {{searchData.hotel_details.phone}}
                                        </div>
                                        <div class="pb-3">
                                            <v-icon class="">location_on</v-icon>
                                            {{searchData.hotel_details.address1}},
                                            {{searchData.hotel_details.address2}}, {{searchData.hotel_details.city}},
                                            {{searchData.hotel_details.state}}
                                        </div>

                                        <template>
                                            <div class="text-xs-center pb-4">
                                                    <span v-for="(item, i) in searchData.hotel_details.amenities.length"
                                                          :key="i"
                                                    >
                                                        <v-chip :color="colorList[i%4]" text-color="white">
                                                            {{searchData.hotel_details.amenities[i]}}
                                                        </v-chip>
                                                    </span>

                                            </div>
                                        </template>
                                        <div><a :href="searchData.terms_and_conditions_url" target="_blank">Terms and
                                            Conditions</a></div>
                                    </div>
                                </v-card-title>
                            </v-flex>
                        </v-layout>

                        <v-divider light></v-divider>

                        <!--Rooms and more details-->
                        <v-expansion-panel v-model="expandPanel"
                                           expand>
                            <v-expansion-panel-content>
                                <template v-slot:actions>
                                    <v-icon color="primary"> $vuetify.icons.expand</v-icon>
                                </template>

                                <template v-slot:header>
                                    <div>Rooms and more details</div>
                                </template>

                                <v-card class="white--text">
                                    <template>
                                        <div>
                                            <v-tabs
                                                    v-model="active"
                                                    color="blue"
                                                    dark
                                                    slider-color="blue lighten-3"
                                            >
                                                <v-tab key="1" ripple>
                                                    Available rooms
                                                </v-tab>
                                                <v-tab key="2" ripple>
                                                    Customer support
                                                </v-tab>

                                                <v-tab-item>
                                                    <v-card flat>
                                                        <rooms-grid :roomsData="searchData.room_types_array"></rooms-grid>
                                                    </v-card>
                                                </v-tab-item>

                                                <v-tab-item>
                                                    <v-card flat>
                                                        <custome-support :supportData="searchData.customer_support"></custome-support>
                                                    </v-card>
                                                </v-tab-item>
                                            </v-tabs>
                                        </div>
                                    </template>
                                </v-card>
                            </v-expansion-panel-content>
                        </v-expansion-panel>
                    </v-card>
                </v-flex>
            </v-layout>
        </v-container>
    </v-card>
</template>

<script>
  import roomsGrid from './RoomsGrid'
  import customeSupport from './CustomerSupport'

  export default {

    components: {
      roomsGrid,
      customeSupport
    },

    name: 'Hotel',
    props: ['searchData'],

    data: () => ({
      colorList: ['primary', 'secondary', 'red', 'green'],
      active: null,
      text: '',
      expandPanel: [true]
    }),

    methods: {
      isDataAvailable () {
        return (this.searchData !== '')
      }
    }
  }
</script>

<style scoped>

</style>

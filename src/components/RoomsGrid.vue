<template>
    <v-layout>
        <v-flex xs12>
            <v-card>
                <v-container
                        fluid
                        grid-list-lg
                >
                    <v-layout row wrap>
                        <v-flex
                                v-for="card in roomsData"
                                xs6
                        >
                            <v-card>
                                <v-img
                                        :src="card['photos'][0]['url']"
                                        height="200px"
                                >
                                    <v-container
                                            fill-height
                                            fluid
                                            pa-2
                                    >
                                        <v-layout fill-height>
                                            <v-flex xs12 align-end flexbox>

                                                <v-chip color="blue" text-color="white">
                                                    {{card.final_price_at_booking.amount}} {{card.final_price_at_booking.currency}}
                                                </v-chip>
                                                <span class="headline white--text" v-text=""></span>
                                            </v-flex>
                                        </v-layout>
                                    </v-container>
                                </v-img>

                                <v-card-title primary-title>
                                    <div>
                                        <h3 class="headline mb-0">{{card.name}}</h3>
                                        <div> {{ card.description }} </div>
                                    </div>
                                </v-card-title>


                                <v-card-actions>

                                    <v-spacer></v-spacer>

                                    <template>
                                        <div class="text-xs-center">
                                            <span v-for="(item, i) in card.value_adds.length"
                                                  :key="i"
                                            >
                                            <v-chip outline color="primary">{{card.value_adds[i]}}</v-chip>
                                            </span>
                                        </div>
                                    </template>
                                </v-card-actions>

                            </v-card>

                        </v-flex>
                    </v-layout>
                </v-container>
            </v-card>
        </v-flex>
    </v-layout>
</template>

<script>
  export default {
    name: 'RoomsGrid',
    props: ['roomsData'],

    data: () => ({
      cards: [
        { title: 'Pre-fab homes', src: 'https://cdn.vuetifyjs.com/images/cards/house.jpg', flex: 12 },
        { title: 'Favorite road trips', src: 'https://cdn.vuetifyjs.com/images/cards/road.jpg', flex: 6 },
        { title: 'Best airlines', src: 'https://cdn.vuetifyjs.com/images/cards/plane.jpg', flex: 6 }
      ]
    })
  }
</script>

<style scoped>

</style>

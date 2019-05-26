<template>
    <v-form
            ref="form"
            v-model="valid"
            lazy-validation
    >
    <v-card>
        <v-card-title class="grey lighten-4 py-4 title">
            Select your criteria
        </v-card-title>

        <v-container grid-list-lg  class="pa-4">
            <v-layout row wrap>
                <v-flex xs6>
                    <date
                            label="Start date"
                            @dateSelected="startDate = $event"
                    ></date>
                </v-flex>

                <v-flex xs6>
                    <date
                            label="End date"
                            @dateSelected="endDate = $event" ></date>
                </v-flex>

                <v-flex xs6>
                    <v-select
                            v-model="langSelect"
                            :items="langItems"
                            :rules="[v => !!v || 'Item is required']"
                            label="Language"
                            prepend-icon="language"
                            required
                    ></v-select>
                </v-flex>

                <v-flex xs6>
                    <v-select
                            v-model="currencySelect"
                            :items="currencyItems"
                            :rules="[v => !!v || 'Item is required']"
                            label="Currency"
                            prepend-icon="attach_money"
                            required
                    ></v-select>
                </v-flex>

                <v-flex xs12>
                    <v-card-actions>
                        <v-spacer></v-spacer>


                        <v-btn
                                :disabled="!valid"
                                color="success"
                                @click="validate"
                        >
                            Search
                        </v-btn>
                    </v-card-actions>
                </v-flex>
            </v-layout>
        </v-container>

    </v-card>
    </v-form>
</template>

<script>
  import date from './DatePicker'
  export default {

    components: {
      date
    },

    data: () => ({
      valid: true,
      langSelect: null,
      currencySelect: null,
      startDate: new Date().toISOString().substr(0, 10),
      endDate: new Date().toISOString().substr(0, 10),
      langItems: [
        'en_US',
        'en_CA',
        'ar_AE',
        'fr_FR',
        'ru_RU'
      ],
      currencyItems: [
        'USD',
        'EUR',
        'AED',
        'PKR'
      ]
    }),

    methods: {
      validate () {
        if (this.$refs.form.validate()) {
          this.snackbar = true;
          this.performSearch();
        }
      },
      performSearch() {

        const searchParams = new URLSearchParams();

        searchParams.append("api_version", "1");
        searchParams.append("hotel", '{"item_id": 1,"partner_reference": "abc123"}');
        searchParams.append("start_date", this.startDate);
        searchParams.append("end_date", this.endDate);
        searchParams.append("party", '[{ "adults": 2, "children": [1] }]');
        searchParams.append("lang", this.langSelect);
        searchParams.append("currency", this.currencySelect);
        searchParams.append("user_country", "US");

        fetch('https://tbec-mock-advertiser-qa.dus.tcs.trivago.cloud/api/v1/booking_availability', {
          method: 'post',
          headers: {
            "Content-type": "application/x-www-form-urlencoded",
            "Authorization": 'Basic ' + Buffer.from("qa:case_study").toString('base64')
        },
          body: searchParams
        }).then(res => res.json())
          .then(res => {
            this.$emit('onDataLoad', res);
          })
          .catch(err => console.log(err));
      }
      /*,
      resetValidation () {
        this.$refs.form.resetValidation()
      }*/
    }
  }
</script>

<style scoped>

</style>

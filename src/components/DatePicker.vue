<template>
    <v-layout row wrap>
        <v-flex xs12>
            <v-menu
                    v-model="menu2"
                    :close-on-content-click="false"
                    :nudge-right="40"
                    lazy
                    transition="scale-transition"
                    offset-y
                    full-width
                    min-width="290px"
            >
                <template v-slot:activator="{ on }">
                    <v-text-field
                            v-model="date"
                            :label="label"
                            prepend-icon="event"
                            readonly
                            v-on="on"
                    ></v-text-field>
                </template>
                <v-date-picker v-model="date" @input="onDateSelect"></v-date-picker>
            </v-menu>
        </v-flex>
        <v-spacer></v-spacer>
    </v-layout>
</template>

<script>
  export default {
    props: ['label'],
    data: () => ({
      date: new Date().toISOString().substr(0, 10),
      menu: false,
      modal: false,
      menu2: false
    }),
    methods: {
      onDateSelect () {
        this.menu2 = false;
        this.$emit('dateSelected', this.date);
      }
    }
  }
</script>

<style scoped>

</style>

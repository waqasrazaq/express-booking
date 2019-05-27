<template>
    <v-expansion-panel>

        <v-expansion-panel-content
        >
            <template v-slot:header>
                <div>Phones</div>
            </template>
            <v-card>
                <v-card-text
                        v-for="(item,i) in supportData.phone_numbers"
                        :key="i">{{item.contact}}
                </v-card-text>
            </v-card>
        </v-expansion-panel-content>

        <v-expansion-panel-content>
            <template v-slot:header>
                <div>Emails</div>
            </template>
            <v-card>
                <v-card-text
                        v-for="(item,i) in supportData.emails"
                        :key="i">{{item.contact}}
                </v-card-text>
            </v-card>
        </v-expansion-panel-content>

    </v-expansion-panel>
</template>

<script>
  export default {
    name: 'CustomerSupport',
    props: ['supportData']
  }
</script>

<style scoped>

</style>

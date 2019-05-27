<template>
  <v-app>
    <v-toolbar app>
      <img
              src="http://developer.trivago.com/img/wabi_small.png"
              height="50px"
              width="50px"
      />
      <v-spacer></v-spacer>
      <v-toolbar-title class="headline text-uppercase">
        <span class="iconify" data-icon="logos-vuetifyjs" data-inline="false"></span>
        <span>Trivago</span>
        <span class="font-weight-light">&nbsp;Express Booking</span>
      </v-toolbar-title>
    </v-toolbar>
    <v-content>
          <search-form @onDataLoad="searchData=$event"></search-form>
          <search-result :searchData="searchData"></search-result>
    </v-content>
  </v-app>
</template>

<script>
import searchForm from './components/SeacrhForm'
import searchResult from './components/SearchResult'

export default {
  name: 'App',
  components: {
    searchForm,
    searchResult
  },
  data () {
    return {
      searchData: ''
    }
  }
}
</script>

<template>
  <v-app dark>
    <v-toolbar dark app>
      <v-toolbar-title class="headline text-uppercase">
        <span>PetApp</span>
        <span class="font-weight-light">Adopt A Pet</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items>
      <v-btn flat to="/">Home</v-btn>
      <v-btn flat to="/cats">Cats</v-btn>
      <v-btn flat to="/dogs">Dogs</v-btn>
    </v-toolbar-items>
    </v-toolbar>

    <v-content>
  <v-container grid-list-md text-xs-center>
    <v-layout row wrap>
      <v-flex xs12>
        <router-view/>
      </v-flex>
    </v-layout>
  </v-container>

    </v-content>
  </v-app>
</template>

<script>
export default {
  name: 'App',
  components: {

  },
  data () {
    return {
      //
    }
  }
}
</script>

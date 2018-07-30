<template>
  <v-layout row>
    <v-flex xs12 sm3 offset-sm1 v-for="i in 3">
      <v-card>
        <link href='https://fonts.googleapis.com/css?family=Roboto:300,400,500,700|Material+Icons' rel="stylesheet">
        <v-card-media
          src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
          height="200px"
        >
        </v-card-media>

        <v-card-title primary-title class="link">
          <div>
            <div class="headline">{{items[i].link}}</div>
            <span class="grey--text">{{items[i].title}}</span>
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

          </v-card-text>
        </v-slide-y-transition>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
  export default {
    name: "NewsCard",
    props:['items'],
    data() {
      show:false
    }
  }
</script>

<style scoped>
  .link{
    overflow: auto;
  }
  .headline{

  }
</style>

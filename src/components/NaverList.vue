<template>
  <v-layout row wrap align-center>
    <v-flex v-for="item in tophun" :key="item.title">
      <v-card width="900px" height="40px" style="line-height: 10px;">
        <a v-bind:href="item.link" style="text-decoration: none; color: black;">
          <v-card-text>{{item.title}}</v-card-text>
        </a>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
  export default {
    name: "NaverList",
    props: ["tophun", "links"],
    methods: {
      linking: function (link) {
        window.open(link);
      }
    }
  }
</script>

<style scoped>

</style>

<template>
  <v-container fluid grid-list-md>
    <v-data-iterator
      :items="items"
      :rows-per-page-items="rowsPerPageItems"
      :pagination.sync="pagination"
      content-tag="v-layout"
      row
      wrap
    >
      <v-flex
        slot="item"
        slot-scope="props"
        xs12
        sm6
        md4
        lg2
      >
        <v-card>
          <link href='https://fonts.googleapis.com/css?family=Roboto:300,400,500,700|Material+Icons' rel="stylesheet">
          <v-card-media
            class="white--text"
            height="200px"
            src="https://cdn.vuetifyjs.com/images/cards/docks.jpg"
            @click="linking(props.item.link)"
          >
            <v-container fill-height fluid>
              <v-layout fill-height>
                <v-flex xs12 align-end flexbox>
                  <span class="headline">{{ props.item.title }}</span>
                </v-flex>
              </v-layout>
            </v-container>
          </v-card-media>
          <v-card-title>
            <div>
              <span class="grey--text"></span><br>
            </div>
          </v-card-title>
        </v-card>
      </v-flex>
    </v-data-iterator>
  </v-container>
</template>

<script>
  export default {
    name: "NewsCard",
    props: ['items'],
    data: () => ({
      rowsPerPageItems: [5, 10, 15],
      pagination: {
        rowsPerPage: 5
      },
    }),
    methods:{
      linking:function (link) {
        window.open(link);
      }
    }
  }
</script>

<style scoped>

</style>

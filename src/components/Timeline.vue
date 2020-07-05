<template>
  <div>
  <div v-for="(article, itemObjKey) in articles" :key="article.title">
  <v-card
    :loading="loading"
    class="mx-auto my-12"
    max-width="95%"
    elevation="24"
  >
    <v-img
      height="450"
      v-bind:src="article.urlToImage"
    ></v-img>

    <v-card-title> {{ article.title }}</v-card-title>

    <v-card-text>
      <v-row
        align="center"
        class="mx-0"
      >
       <v-col cols="12" sm="3">
            <v-btn icon color="pink">
              <v-icon>mdi-heart</v-icon>
              <div class="grey--text ml-4">{{itemObjKey + 1}}</div>
            </v-btn>
      </v-col>
      </v-row>

      <h2 class="red--text text--lighten-1"> {{ article.source.name }} </h2>

      <div> {{ article.description }} 
      <a :href="article.url" :target="_blank">
      <v-btn text x-small color="white">
      Read more</v-btn>
      </a>
      </div>
    </v-card-text>

    <v-divider class="mx-4"></v-divider>

    <v-card-title> 
      <div v-if="article.author">
       Author : {{ article.author }}
      </div>
      <div v-else>
        Author : Unknown
      </div>
    </v-card-title>

    <v-card-text>
      <v-chip-group
        v-model="selection"
        active-class="deep-purple accent-4 white--text"
        column
      >
        <v-chip>5:30PM</v-chip>

        <v-chip>7:30PM</v-chip>

        <v-chip>8:00PM</v-chip>

        <v-chip>9:00PM</v-chip>
      </v-chip-group>
    </v-card-text>

    <v-card-actions>
      <v-btn color="error" fab x-small dark>
                <v-icon>mdi-alarm</v-icon>
      </v-btn>
            Published on : {{ article.publishedAt }}
    </v-card-actions>
  </v-card>
  </div>
  </div>
</template>

<script>
export default {
  props: {
      articles: Array
  },
  data: () => ({
      loading: false,
      selection: 1,
  }),
  methods: {
    reserve () {
      this.loading = true

      setTimeout(() => (this.loading = false), 2000)
    },
  },
}
</script>
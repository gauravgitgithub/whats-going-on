<template>
  <div>
  <div v-for="(article, itemObjKey) in articles" :key="article.title">
  <v-card
    class="mx-auto"
    max-width="100%"
    elevation="24"
  >
    <v-img
      class="white--text align-end"
      height="450px"
      v-bind:src="article.urlToImage"
    >
      <v-card-title>{{ article.title }}</v-card-title>
    </v-img>

    <v-card-subtitle class="pb-0">#{{itemObjKey + 1}}</v-card-subtitle>

    <v-card-text class="text--primary">
      <div>{{ article.source.name }} </div>

      <div>{{ article.description }}</div>
    </v-card-text>

    <v-card-actions>
      <v-btn
        color="orange"
        text
      >
        Share
      </v-btn>

      <v-btn
        color="orange"
        text
      >
        Explore
      </v-btn>
    </v-card-actions>
  </v-card>
  <br/>
  </div>
  </div>
</template>
<script>
export default {
  props: {
      articles: Array
  },
}
</script>
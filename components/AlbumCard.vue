<template>
  <v-flex xs12 lg4>
    <v-card class="ma-3">
      <v-card-title class="headline">{{ album.title }}</v-card-title>
      <v-card-actions>
        <v-spacer></v-spacer>
        <v-btn small color="primary" dark nuxt :to="`/albums/${album.id}`">Ver album</v-btn>
      </v-card-actions>
    </v-card>
  </v-flex>
</template>
<script>
  export default {
    name: 'AlbumCard',
    props: {
      album: Object
    }
  }
</script>
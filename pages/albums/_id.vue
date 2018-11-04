<template lang="html">
  <v-layout row wrap>
    <v-flex xs12 text-xs-center>
      <h1>{{ album.title }}</h1>
    </v-flex>
    <v-flex xs12 lg6 v-for="photo in photos" :key="photo.id">
      <v-card class="ma-3">
        <v-img
          :src="photo.url"
          aspect-ratio="2.75"
        ></v-img>

        <v-card-title primary-title>
          <div>
            <h3 class="headline mb-0">{{ photo.title }}</h3>
          </div>
        </v-card-title>
      </v-card>
    </v-flex>
  </v-layout>
</template>
<script>
// import router from 'vue-router'
import axios from 'axios'
import env from '../../config/env.js'

export default {
  name: 'AlbumSingle',
  data () {
    return {
      album: {},
      photos: []
    }
  },
  created () {
    axios.get(`${env.endpoint}/albums/${this.$route.params.id}`).then(response => {
      this.album = response.data
    })

    axios.get(`${env.endpoint}/albums/${this.$route.params.id}/photos`).then(response => {
      this.photos = response.data
    })
  }
}
</script>

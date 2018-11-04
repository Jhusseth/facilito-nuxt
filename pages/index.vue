<template>
  <v-layout row wrap>
    <AlbumCard :album='album' v-for="album in albums" :key="album.id"/>
  </v-layout>
</template>

<script>
import axios from 'axios'
import env from '../config/env.js'
import AlbumCard from '../components/AlbumCard.vue'

export default {
  data () {
    return {
      albums: []
    }
  },
  created () {
    axios.get(`${env.endpoint}/albums`).then(response => {
      this.albums = response.data
    })
  },
  components: {
    AlbumCard
  }
}
</script>

<script setup lang="ts">
import type { Song } from '../types'

defineProps<{
  song: Song | null
}>()
</script>

<template>
  <section>
    <h2>NowPlaying</h2>

    <div v-if="song" class="now-playing">
      <img :src="song.image_url" :alt="song.title" />

      <h3>{{ song.title }}</h3>
      <p>{{ song.artist }}</p>
      <p>♫ Now Playing</p>
    </div>

    <p v-else>
      Please select a song from the PlayList.
    </p>
  </section>
</template>

<style scoped>
.now-playing {
  text-align: center;
  padding: 20px;
  border: 1px solid #42b883;
  border-radius: 12px;
}

img {
  width: 180px;
  height: 180px;
  object-fit: cover;
  border-radius: 10px;
}

h3 {
  margin-bottom: 5px;
}
</style>

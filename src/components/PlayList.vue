<script setup lang="ts">
import type { Song } from '../types'

defineProps<{
  playlist: Song[]
}>()

const emit = defineEmits<{
  (event: 'play-song', song: Song): void
}>()
</script>

<template>
  <section>
    <h2>PlayList ({{ playlist.length }})</h2>

    <p v-if="playlist.length === 0">
      Please pick a song from the SongList.
    </p>

    <div
      v-for="song in playlist"
      :key="song.song_id"
      class="song"
      @click="emit('play-song', song)"
    >
      <img :src="song.image_url" :alt="song.title" />

      <div>
        <h3>{{ song.title }}</h3>
        <p>{{ song.artist }}</p>
      </div>

      <button>▶ Play</button>
    </div>
  </section>
</template>

<style scoped>
.song {
  display: flex;
  align-items: center;
  gap: 15px;
  padding: 12px;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  border-radius: 8px;
  cursor: pointer;
}

.song:hover {
  background-color: #e0f2e9;
}

img {
  width: 60px;
  height: 60px;
  object-fit: cover;
  border-radius: 6px;
}

button {
  margin-left: auto;
  cursor: pointer;
}
</style>

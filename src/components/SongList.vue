<script setup lang="ts">
import type { Song } from '../types'

defineProps<{
  songs: Song[]
}>()

const emit = defineEmits<{
  (event: 'add-song', song: Song): void
}>()
</script>

<template>
  <section>
    <h2>SongList</h2>

    <div
      v-for="song in songs"
      :key="song.song_id"
      class="song"
      @click="emit('add-song', song)"
    >
      <img :src="song.image_url" :alt="song.title" />

      <div>
        <h3>{{ song.title }}</h3>
        <p>{{ song.artist }}</p>
      </div>

      <button>Add +</button>
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
  background-color: #eeeeee;
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

<script setup lang="ts">
import { ref } from 'vue'
import type { Song } from './types'

import SongList from './components/SongList.vue'
import PlayList from './components/PlayList.vue'
import NowPlaying from './components/NowPlaying.vue'

const songs: Song[] = [
  {
    title: 'A Love Theme',
    artist: 'Mixkit',
    song_id: 1,
    image_url: 'https://picsum.photos/seed/music1/200'
  },
  {
    title: 'Hazy After Hours',
    artist: 'Mixkit',
    song_id: 2,
    image_url: 'https://picsum.photos/seed/music2/200'
  },
  {
    title: 'Vastness',
    artist: 'Mixkit',
    song_id: 3,
    image_url: 'https://picsum.photos/seed/music3/200'
  }
]

const playlist = ref<Song[]>([])
const nowPlaying = ref<Song | null>(null)

function addSong(song: Song) {
  const exists = playlist.value.some(
    item => item.song_id === song.song_id
  )

  if (!exists) {
    playlist.value.push(song)
  }
}

function playSong(song: Song) {
  nowPlaying.value = song
}
</script>

<template>
  <main>
    <header>
      <h1>My Music Playlist</h1>
      <p>InnoTech Assignment W13D</p>
    </header>

    <div class="music-container">
      <SongList
        :songs="songs"
        @add-song="addSong"
      />

      <PlayList
        :playlist="playlist"
        @play-song="playSong"
      />

      <NowPlaying
        :song="nowPlaying"
      />
    </div>
  </main>
</template>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #f0f4f8;
  color: #1e293b;
}

header {
  background: #172554;
  color: white;
  text-align: center;
  padding: 30px;
}

header h1 {
  margin: 0;
}

.music-container {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 20px;
  max-width: 1400px;
  margin: 30px auto;
  padding: 20px;
}

section {
  background: white;
  padding: 20px;
  border-radius: 12px;
  box-shadow: 0 4px 12px #00000015;
}

button {
  background: #15803d;
  color: white;
  border: none;
  padding: 10px;
  border-radius: 6px;
  cursor: pointer;
}

button:hover {
  background: #166534;
}

@media (max-width: 900px) {
  .music-container {
    grid-template-columns: 1fr;
  }
}
</style>

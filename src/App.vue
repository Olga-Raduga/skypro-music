<script setup>
import { computed, ref } from 'vue'
import Navbar from './components/Navbar.vue'
import FilterControls from './components/FilterControls.vue'
import Playlist from './components/Playlist.vue'
import PlayerBar from './components/PlayerBar.vue'
import { tracks } from './data/tracks.js'
const search = ref('')
const visibleTracks = computed(() => {
  const query = search.value.trim().toLocaleLowerCase('ru-RU')
  if (!query) return tracks
  return tracks.filter((track) =>
    `${track.title} ${track.author}`
      .toLocaleLowerCase('ru-RU')
      .includes(query)
  )
})
const playlistImages = [
  '/img/playlist01.png',
  '/img/playlist02.png',
  '/img/playlist03.png',
]
</script>

<template>
  <div id="top" class="app-shell">
    <main class="main">
      <Navbar />
      <section class="main__centerblock centerblock">
        <FilterControls v-model:search="search" />
        <h1 class="centerblock__h2">Треки</h1>
        <Playlist
          id="tracks"
          :tracks="visibleTracks"
        />
      </section>
      <aside id="playlists" class="main__sidebar sidebar">
        <div class="sidebar__personal">
          <p class="sidebar__personal-name">Skypro.Music</p>
        </div>
        <div class="sidebar__list">
          <div
            v-for="image in playlistImages"
            :key="image"
            class="sidebar__item"
          >
            <img class="sidebar__img" :src="image" alt="Обложка плейлиста">
          </div>
        </div>
      </aside>
    </main>
    <PlayerBar :track="tracks[0]" />
  </div>
</template>
<style scoped>
.app-shell {
  min-height: 100vh;
  color: #fff;
  background: #181818;
  font-family: 'Montserrat', sans-serif;
}
.main {
  display: grid;
  grid-template-columns: 244px minmax(0, 1fr) 280px;
  max-width: 1920px;
  min-height: 100vh;
  margin: 0 auto;
  padding-bottom: 78px;
}
.main__centerblock {
  -webkit-box-flex: 1;
  -ms-flex: 1 1 auto;
  flex: 1 1 auto;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -ms-flex-wrap: wrap;
  flex-wrap: wrap;
  -webkit-box-pack: justify;
  -ms-flex-pack: justify;
  justify-content: space-between;
}
.centerblock__h2 {
  font-style: normal;
  font-weight: 400;
  font-size: 64px;
  line-height: 72px;
  letter-spacing: -0.8px;
  margin-bottom: 45px;
}
.main__sidebar {
  max-width: 418px;
  padding: 20px 90px 20px 78px;
}
.sidebar__personal {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-orient: horizontal;
  -webkit-box-direction: normal;
  -ms-flex-direction: row;
  flex-direction: row;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
  -webkit-box-pack: end;
  -ms-flex-pack: end;
  justify-content: flex-end;
  padding: 12px 0 15px 0;
}

.sidebar__personal-name {
  font-style: normal;
  font-weight: 400;
  font-size: 16px;
  line-height: 24px;
  color: #ffffff;
  margin-right: 16px;
}

.sidebar__icon {
  width: 43px;
  height: 43px;
  background-color: #313131;
  border-radius: 50%;
  cursor: pointer;
}

.sidebar__block {
  height: 100%;
  padding: 240px 0 0 0;
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
  -ms-flex-direction: column;
  flex-direction: column;
  -webkit-box-pack: start;
  -ms-flex-pack: start;
  justify-content: flex-start;
}

.sidebar__list {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
  -ms-flex-direction: column;
  flex-direction: column;
  -webkit-box-align: center;
  -ms-flex-align: center;
  align-items: center;
}

.sidebar__item {
  width: 250px;
  height: 150px;
}

.sidebar__item:not(:last-child) {
  margin-bottom: 30px;
}

.sidebar__link {
  width: 100%;
  height: 100%;
}

.sidebar__img {
  width: 100%;
  height: auto;
}

.wrapper {
  width: 100%;
  min-height: 100%;
  overflow: hidden;
  background-color: #383838;
}

.container {
  max-width: 1920px;
  height: 100vh;
  margin: 0 auto;
  position: relative;
  background-color: #181818;
}
@media (max-width: 1100px) {
  .main {
    grid-template-columns: 200px minmax(0, 1fr);
  }
  .main__sidebar {
    display: none;
  }
  .main__centerblock {
    padding: 20px 28px;
  }
}
@media (max-width: 720px) {
  .main {
    grid-template-columns: minmax(0, 1fr);
  }
  .main__centerblock {
    padding: 16px;
  }
}
</style>

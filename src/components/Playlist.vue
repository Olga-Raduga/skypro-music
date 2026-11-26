<script setup>
import Track from './Track.vue'
defineProps({
  tracks: {
    type: Array,
    default: () => [],
  },
})
</script>
<template>
  <section class="centerblock__content playlist-content">
    <div class="playlist-scroll">
      <div class="content__title playlist-title">
        <div class="playlist-title__col col01">Трек</div>
        <div class="playlist-title__col col02">Исполнитель</div>
        <div class="playlist-title__col col03">Дата</div>
        <div class="playlist-title__col col04">Длительность</div>
      </div>
    </div>
    
    <div class="content__playlist playlist">
      <Track
        v-for="track in tracks"
        :key="track.author + '-' + track.title"
        :track="track"
      />
      <p v-if="tracks.length === 0" class="playlist__empty">
        Треки не найдены
      </p>
    </div>
  </section>
</template>
<style scoped>
.centerblock__content {
  display: flex;
  flex-direction: column;
  width: 100%;
  min-width: 0;
}
.playlist-scroll {
  width: 100%;
  min-width: 0;
  overflow-x: auto;
}
.content__title,
.content__playlist {
  width: 100%;
  min-width: 620px;
}
.content__title {
  display: grid;
  grid-template-columns: minmax(0, 2fr) minmax(0, 1.45fr) minmax(0, 1fr) minmax(100px, 0.85fr);
  gap: 12px;
  align-items: center;
  margin-bottom: 24px;
}
.playlist-title__col {
  min-width: 0;
}
.col04 {
  text-align: right;
  white-space: nowrap;
}

.playlist-title__svg {
  width: 12px;
  height: 12px;
  fill: transparent;
  stroke: #696969;
}
.content__playlist {
  display: flex;
  flex-direction: column;
  overflow-y: auto;
}
</style>
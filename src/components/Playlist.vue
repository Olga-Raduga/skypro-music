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
    <div class="content__title playlist-title">
      <div class="playlist-title__col col01">Трек</div>
      <div class="playlist-title__col col02">Исполнитель</div>
      <div class="playlist-title__col col03">Дата</div>
      <div class="playlist-title__col col04">Длительность</div>
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
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
  -ms-flex-direction: column;
  flex-direction: column;
}
.content__title {
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
  -webkit-box-pack: justify;
  -ms-flex-pack: justify;
  justify-content: space-between;
  margin-bottom: 24px;
}
.playlist-title__col {
  font-style: normal;
  font-weight: 400;
  font-size: 14px;
  line-height: 24px;
  letter-spacing: 2px;
  color: #696969;
  text-transform: uppercase;
}

.playlist-title__svg {
  width: 12px;
  height: 12px;
  fill: transparent;
  stroke: #696969;
}
.content__playlist {
  display: -webkit-box;
  display: -ms-flexbox;
  display: flex;
  -webkit-box-orient: vertical;
  -webkit-box-direction: normal;
  -ms-flex-direction: column;
  flex-direction: column;
  overflow-y: auto;
}
</style>
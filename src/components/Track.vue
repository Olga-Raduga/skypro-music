<script setup>
import { computed } from 'vue'
const props = defineProps({
track: {
type: Object,
required: true,
},
})
const formattedDate = computed(() => {
const [year, month, day] = props.track.date.split('-').map(Number)
const date = new Date(year, month - 1, day, 12)
return new Intl.DateTimeFormat('ru-RU').format(date)
})
</script>
<template>
<article class="playlist__item">
<div class="playlist__track track">
<div class="track__title">
<img
class="track__title-image"
src="/img/icon/note.svg"
alt=""
>
<span class="track__title-link">{{ props.track.title }}</span>
</div>
<div class="track__author">
<span class="track__author-link">{{ props.track.author }}</span>
</div>
<div class="track__date">{{ formattedDate }}</div>
<div class="track__time">
<span class="track__time-text">{{ props.track.duration }}</span>
</div>
</div>
</article>
</template>
<style scoped>
.playlist__item {
  width: 100%;
  min-width: 0;
  margin-bottom: 12px;
}

.playlist__track {
  display: grid;
  grid-template-columns: minmax(0, 2fr) minmax(0, 1.45fr) minmax(0, 1fr) minmax(100px, 0.85fr);
  gap: 12px;
  align-items: center;
  width: 100%;
  min-width: 620px;
}
.track__title {
  display: flex;
  align-items: center;
  width: auto;
  min-width: 0;
}

.track__title-image {
  flex: 0 0 51px;
  width: 51px;
  height: 51px;
  margin-right: 17px;
}

.track__title-svg {
  width: 18px;
  height: 17px;
  fill: transparent;
  stroke: #4e4e4e;
}

.track__title-link {
  min-width: 0;
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  color: #ffffff;
}

.track__title-span {
  font-style: normal;
  font-weight: 400;
  font-size: 16px;
  line-height: 24px;
  color: #4e4e4e;
}

.track__author {
   display: block;
  width: auto;
  min-width: 0;
  overflow: hidden;
}

.track__author-link {
  display: block;
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}

.track__album {
  width: 245px;
}

.track__album-link {
  font-style: normal;
  font-weight: 400;
  font-size: 16px;
  line-height: 24px;
  color: #696969;
}

.track__time-svg {
  width: 14px;
  height: 12px;
  margin-right: 17px;
  fill: transparent;
  stroke: #696969;
}
.track__date {
  min-width: 0;
  color: #696969;
  white-space: nowrap;
}
.track__time {
  min-width: 100px;
  text-align: right;
  white-space: nowrap;
}
.track__time-text {
  font-style: normal;
  font-weight: 400;
  font-size: 16px;
  line-height: 24px;
  text-align: right;
  color: #696969;
}
</style>

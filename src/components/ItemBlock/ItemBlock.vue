<template>
  <div class="info" :class="{active: open}">
    <img @click="$emit('close')" src="@/assets/images/close.svg" alt="" class="info__close">
    <div class="info__block" v-if="current">
        <img :src="current.backdrop_path ? imgUrlFull + current.backdrop_path : current.poster_path ? imgUrlFull + current.poster_path : NOPHOTO" alt="" class="info__block-img">
        <div class="info__block-content">
            <div class="info__block-data">
                <h2 class="info__block-data-title">{{ current.title || current.name }}</h2>
                <p class="info__block-data-text">{{ current.overview || 'Нет описания' }}</p>
                <p class="info__block-data-descr">
                    <span>{{ getYear }}</span>
                    <span>{{ getGenres }}</span>
                    <span>{{ getTime }}</span>
                </p>
                <Actors :type="type" :id="current.id" count="4"/>
                <BtnMore  :type="type" :id="current.id"/>
            </div>
        </div>
    </div>
  </div>
</template>

<script setup>
import { imgUrlFull } from '@/url.js';
import NOPHOTO from '@/assets/images/NOPHOTO.png'
import { computed } from 'vue';
const props = defineProps(['open', 'current', 'type'])

const getYear = computed(()=> new Date(props.current.release_date).getFullYear() || new Date(props.current.first_air_date).getFullYear() )

const getGenres = computed(()=> props.current.genres.reduce((acc, item) => acc + `, ${item.name}`, ''))


const getTime = computed(()=>  {
  if(props.type == 'tv' && props.current.episode_run_time.length == 0){
    return ''
  }
  let minutes = 
  props.type == 'movie' ? props.current.runtime :
  props.type == 'tv' ? props.current.episode_run_time[0] : '';
  let hours = Math.floor(minutes / 60) 
  let leftMinetes = minutes % 60
  if(hours == 0){
    return `${leftMinetes}m`
  }else {
    return `${hours}h ${leftMinetes}m`
  }

})

</script>

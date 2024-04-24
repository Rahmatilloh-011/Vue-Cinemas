<template>
  <router-link :to="type + '/' + item.id" class="main__content-list-item">
    <img v-lazy="item.backdrop_path ? imgUrlFull + item.backdrop_path : item.poster_path ? imgUrlFull + item.poster_path : NOPHOTO" alt="" class="main__content-list-item-img">
    <h2 class="main__content-list-item-name">{{ item.name || item.title }}</h2>
  </router-link>
</template>

<script setup>
import { imgUrlFull } from '@/url.js'
import NOPHOTO from '@/assets/images/NOPHOTO.png'
const props = defineProps(['item', 'type'])
</script>

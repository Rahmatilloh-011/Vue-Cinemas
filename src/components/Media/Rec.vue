<template>
    <div class="main__rec">
        <div class="container">
            <h2 class="main__rec-title">Рекомендации</h2>
            <div class="main__rec-list">
                <router-link 
                v-for="item in rec"
                :key="item.id"
                :to="`${item.id}`" 
                class="main__rec-list-item"
                >
                    <img v-lazy="item.backdrop_path ? imgUrlFull + item.backdrop_path : item.poster_path ? imgUrlFull + item.poster_path : NOPHOTO" alt="" class="main__rec-list-item-img">
                    <h2 class="main__rec-list-item-name">{{ item.name || item.title }}</h2>
                </router-link>
            </div>
        </div>
    </div>
</template>

<script setup>
import NOPHOTO from '@/assets/images/NOPHOTO.png'
import { imgUrlFull } from "@/url.js";
const props = defineProps({
  rec: Array,
  type: String,
});
</script>


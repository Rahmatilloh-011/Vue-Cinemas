<template>
  <footer className="footer">
    <ul className="footer__list">
      <li v-for="icon in sicial" :key="icon.id">
        <a :href="icon.href ? icon.href : ''" className="footer__link">
          <img :src="icon.url" alt="" />
        </a>
      </li>
    </ul>
    <div className="footer__text">
      <p className="footer__desc">
        © 2022 CINEPHILE. Может содержать информацию, не предназначенную для
        несовершеннолетних
      </p>
      <p className="footer__desc">Данные получены с сайта themoviedb.org</p>
    </div>
    <a href="https://proweb.uz/" className="footer__logo">
      <img src="@/assets/images/proweb.svg" alt="" />
    </a>
  </footer>
</template>

<script setup>
import { ref } from "vue";

const sicial = ref([
    {id: 1, title: 'telegram', url: require('../../assets/images/social/telegram.svg'), href: 'https://t.me/s/proweb'},
    {id: 2, title: 'vk', url: require('@/assets/images/social/vk.svg')},
    {id: 3, title: 'facebook', url: require('@/assets/images/social/facebook.svg'), href: 'https://www.facebook.com/proweb.uz/'},
    {id: 4, title: 'instagram', url: require('@/assets/images/social/instagram.svg'), href: 'https://www.instagram.com/proweb.uz/?hl=ru'},
    {id: 5, title: 'tiktok', url: require('@/assets/images/social/tiktok.svg')},
    {id: 6, title: 'youtube', url: require('@/assets/images/social/youtube.svg'), href: 'https://youtube.com/c/PROWEBuz'},
    {id: 7, title: 'twitter', url: require('@/assets/images/social/twitter.svg')},
    {id: 8, title: 'linkedin', url: require('@/assets/images/social/linkedin.svg')},
])



</script>

<style>
</style>
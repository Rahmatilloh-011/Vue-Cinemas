<template>
  <router-link :to="`${type}/${id}`" class="btn__more">
    <img src="@/assets/images/more.svg" alt="" class="btn__more-img" />
    <span class="btn__more-text">Подробнее</span>
  </router-link>
</template>

<script setup>

const props = defineProps({
  type: String,
  id: Number
})
</script>

<style>

</style>
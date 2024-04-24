<template>
  <div class="pagination">
    <button
      @click="$emit('page', currentPage - 1)"
      :disabled="currentPage == 1"
      class="pagination__btn"
    >
      prev
    </button>
    <div class="pagination__page">
      <h4>Страница</h4>
      <span>
        {{ currentPage }} <span class="pagination__slash">/</span>
        {{ totalPages }}</span
      >
    </div>
    <button
      @click="$emit('page', currentPage + 1)"
      :disabled="currentPage == totalPages"
      class="pagination__btn"
    >
      next
    </button>
  </div>
</template>

<script setup>
const props = defineProps(["currentPage", "totalPages"]);
</script>

<style>

</style>
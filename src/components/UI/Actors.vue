<template>
  <div class="main__info-block-actors actors" v-if="actors">
    <div
      class="main__info-block-actors-item"
      v-for="actor in actors"
      :key="actor.id"
    >
      <img v-lazy="imgUrl + actor.profile_path" alt="" />
      <span>{{ actor.name }}</span>
    </div>
  </div>
</template>

<script setup>
import { useActors } from "@/stores/actors.js";
import { computed } from "vue";
import { imgUrl } from "@/url.js";

const props = defineProps(["type", "id", "count"]);

const actorsStore = useActors();

actorsStore.getActors({ type: props.type, id: props.id });

const actors = computed(() =>
  props.type == "movie"
    ? actorsStore.getActorsMovie(props.count)
    : actorsStore.getActorsTv(props.count)
);
</script>

<style>

</style>
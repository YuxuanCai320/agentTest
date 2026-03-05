<script setup>
defineProps({
  imageSrc: {
    type: String,
    default: '',
  },
  nodeId: {
    type: String,
    default: '',
  },
});
</script>

<template>
  <article class="cover-card" :data-node-id="nodeId">
    <img class="cover-card-image" :src="imageSrc" alt="" loading="lazy" />
  </article>
</template>

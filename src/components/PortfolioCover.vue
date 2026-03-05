<script setup>
import CoverCard from './CoverCard.vue';
import { COVER_CONTENT } from '../constants/coverContent';

const leftColumnCards = COVER_CONTENT.cards.filter((card) => card.id === '303:4' || card.id === '303:7');
const rightColumnCards = COVER_CONTENT.cards.filter((card) => card.id === '303:5' || card.id === '303:6');
</script>

<template>
  <section class="cover-layout" data-node-id="303:2">
    <aside class="cover-hero">
      <div class="cover-user-block" data-node-id="303:12">
        <img class="cover-avatar" :src="COVER_CONTENT.assets.avatar" alt="User avatar" data-node-id="303:11" />

        <div class="cover-user-label" data-node-id="303:14">
          <img class="cover-arrow" :src="COVER_CONTENT.assets.arrow" alt="Arrow" data-node-id="303:13" />
          <span>{{ COVER_CONTENT.userName }}</span>
        </div>
      </div>

      <header class="cover-headline" data-node-id="303:8">
        <h1>
          <span v-for="line in COVER_CONTENT.titleLines" :key="line" class="headline-line">{{ line }}</span>
        </h1>

        <p class="cover-subtitle" data-node-id="303:10">
          <span class="cover-subtitle-arrow">↘</span>
          <span>
            <span v-for="line in COVER_CONTENT.subtitleLines" :key="line" class="subtitle-line">{{ line }}</span>
          </span>
        </p>
      </header>
    </aside>

    <section class="cover-cards" data-node-id="303:3">
      <div class="cover-column cover-column-left">
        <CoverCard
          v-for="card in leftColumnCards"
          :key="card.id"
          :node-id="card.id"
          :image-src="COVER_CONTENT.assets[card.image]"
          :style="{ width: `${card.width}px`, height: `${card.height}px` }"
        />
      </div>

      <div class="cover-column cover-column-right">
        <CoverCard
          v-for="card in rightColumnCards"
          :key="card.id"
          :node-id="card.id"
          :image-src="COVER_CONTENT.assets[card.image]"
          :style="{ width: `${card.width}px`, height: `${card.height}px` }"
        />
      </div>
    </section>
  </section>
</template>

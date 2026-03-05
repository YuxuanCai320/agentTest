<script setup>
import { CASE_STUDY_CONTENT } from '../constants/caseStudyContent';
</script>

<template>
  <article class="case-study-card" data-node-id="303:5">
    <h1 class="case-study-title">{{ CASE_STUDY_CONTENT.title }}</h1>

    <img
      class="case-study-image"
      :src="CASE_STUDY_CONTENT.imageUrl"
      alt="Team discussing product strategy in an office"
      loading="lazy"
    />

    <div class="case-study-copy">
      <p>{{ CASE_STUDY_CONTENT.introTitle }}</p>

      <ul>
        <li v-for="item in CASE_STUDY_CONTENT.marketBullets" :key="item">{{ item }}</li>
      </ul>

      <p>{{ CASE_STUDY_CONTENT.featureBridge }}</p>
      <p>{{ CASE_STUDY_CONTENT.painIntro }}</p>

      <ul>
        <li v-for="item in CASE_STUDY_CONTENT.painBullets" :key="item">{{ item }}</li>
      </ul>

      <p>{{ CASE_STUDY_CONTENT.closing }}</p>
    </div>
  </article>
</template>

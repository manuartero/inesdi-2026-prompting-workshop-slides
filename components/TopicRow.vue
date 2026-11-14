<script setup lang="ts">
// `icon` takes a UnoCSS icon class written literally in the slide, e.g. "i-ph-target-fill",
// so the icon preset can find it when it scans the markdown.
defineProps<{ title?: string; tone?: 'warning'; icon?: string }>()
</script>

<template>
  <div class="topic-row" :class="{ 'topic-row--warning': tone === 'warning' }">
    <b v-if="title" class="topic-row__title">
      <span v-if="icon" class="topic-row__icon"><span :class="icon" /></span>
      {{ title }}
    </b>
    <span class="topic-row__text"><slot /></span>
  </div>
</template>

<style scoped>
.topic-row {
  display: grid;
  grid-template-columns: fit-content(40%) 1fr;
  column-gap: 1.5rem;
  align-items: center;
  padding: 0.5rem 0;
  border-bottom: 1px solid var(--ine-line);
  font-size: 0.9rem;
  line-height: 1.35;
}
.topic-row__title {
  display: flex;
  align-items: center;
  gap: 0.6rem;
  font-weight: 600;
}
.topic-row__icon {
  flex: none;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 1.9rem;
  height: 1.9rem;
  border-radius: 9999px;
  background: var(--ine-yellow);
  color: var(--ine-ink);
  font-size: 1rem;
}
.topic-row__text {
  color: var(--ine-muted);
}
.topic-row--warning {
  border-bottom-color: var(--ine-yellow);
}
.topic-row--warning .topic-row__text {
  color: var(--ine-ink);
}
</style>

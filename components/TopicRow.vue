<script setup lang="ts">
defineProps<{ title?: string; tone?: 'warning' }>()
</script>

<template>
  <div class="topic-row" :class="{ 'topic-row--warning': tone === 'warning' }">
    <b v-if="title" class="topic-row__title">{{ title }}</b>
    <span class="topic-row__text"><slot /></span>
  </div>
</template>

<style scoped>
.topic-row {
  display: grid;
  grid-template-columns: 38% 1fr;
  gap: 1.2rem;
  align-items: baseline;
  padding: 0.5rem 0;
  border-bottom: 1px solid var(--ine-line);
  font-size: 0.9rem;
  line-height: 1.35;
}
.topic-row__title {
  font-weight: 600;
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

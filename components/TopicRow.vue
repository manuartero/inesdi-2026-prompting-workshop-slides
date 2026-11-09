<script setup lang="ts">
defineProps<{ title?: string; tone?: 'warning' }>()
</script>

<template>
  <div class="topic-row" :class="{ 'topic-row--warning': tone === 'warning' }">
    <span class="topic-row__marker" aria-hidden="true" />
    <span>
      <b v-if="title" class="topic-row__title">{{ title }}</b><template v-if="title">: </template><slot />
    </span>
  </div>
</template>

<style scoped>
.topic-row {
  display: flex;
  gap: 0.7rem;
  align-items: baseline;
  background: white;
  padding: 0.45rem 0.9rem;
  font-size: 0.9rem;
  line-height: 1.35;
}
.topic-row__marker {
  flex: 0 0 auto;
  width: 0.5rem;
  height: 0.5rem;
  background: var(--ine-cyan);
  outline: 1px solid var(--ine-ink);
  transform: translateY(-0.05rem);
}
.topic-row__title {
  font-weight: 600;
  color: var(--ine-navy);
}
.topic-row--warning .topic-row__marker {
  background: var(--ine-yellow);
}
</style>

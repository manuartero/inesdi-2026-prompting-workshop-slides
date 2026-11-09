<script setup lang="ts">
defineProps<{ minutes?: string; number?: string }>()
</script>

<template>
  <div class="slidev-layout ine-dark ine-section">
    <span class="ine-cover__stripe" aria-hidden="true" />
    <div class="ine-section__body">
      <p v-if="number" class="ine-section__number">{{ number }}</p>
      <slot />
      <p v-if="minutes" class="ine-section__minutes">{{ minutes }}</p>
    </div>
  </div>
</template>

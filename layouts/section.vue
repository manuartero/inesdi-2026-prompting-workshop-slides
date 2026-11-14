<script setup lang="ts">
defineProps<{ number?: string }>()
</script>

<template>
  <div class="slidev-layout ine-dark ine-section">
    <div class="ine-section__body">
      <p v-if="number" class="ine-section__number">{{ number }}</p>
      <slot />
    </div>
  </div>
</template>

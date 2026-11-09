<script setup lang="ts">
defineProps<{ minutes?: string }>()
</script>

<template>
  <div class="slidev-layout ine-light ine-default">
    <BrandStrip />
    <span v-if="minutes" class="ine-chip">{{ minutes }}</span>
    <div class="ine-default__body">
      <slot />
    </div>
    <footer class="ine-footer">
      <span>{{ $slidev.configs.title }}</span>
      <span>{{ $slidev.nav.currentPage }} / {{ $slidev.nav.total }}</span>
    </footer>
  </div>
</template>

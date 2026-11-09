<script setup lang="ts">
defineProps<{ minutes?: string }>()
</script>

<template>
  <div class="slidev-layout ine-light ine-default">
    <div class="ine-default__body">
      <slot />
      <div class="ine-cols">
        <div><slot name="left" /></div>
        <div><slot name="right" /></div>
      </div>
    </div>
    <footer class="ine-footer">
      <span>{{ $slidev.configs.title }}</span>
      <span>
        <template v-if="minutes">{{ minutes }} min · </template>{{ $slidev.nav.currentPage }}
      </span>
    </footer>
  </div>
</template>

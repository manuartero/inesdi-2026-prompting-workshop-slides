<script setup lang="ts">
defineProps<{ session?: string; teacher?: string }>()
</script>

<template>
  <div class="slidev-layout ine-dark ine-cover">
    <InesdiWordmark light class="ine-cover__brand" />
    <div class="ine-cover__body">
      <slot />
      <span class="ine-rule" aria-hidden="true" />
      <p v-if="session" class="ine-cover__session">{{ session }}</p>
      <p v-if="teacher" class="ine-cover__teacher">{{ teacher }}</p>
    </div>
  </div>
</template>

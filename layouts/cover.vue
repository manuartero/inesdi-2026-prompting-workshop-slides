<script setup lang="ts">
defineProps<{ session?: string; teacher?: string }>()
</script>

<template>
  <div class="slidev-layout ine-dark ine-cover">
    <header class="ine-cover__band">
      <InesdiWordmark />
    </header>
    <span class="ine-cover__stripe" aria-hidden="true" />
    <div class="ine-cover__body">
      <slot />
      <p v-if="session" class="ine-cover__session">{{ session }}</p>
      <p v-if="teacher" class="ine-cover__teacher">Docente: {{ teacher }}</p>
    </div>
  </div>
</template>

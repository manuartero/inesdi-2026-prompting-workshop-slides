<script setup lang="ts">
defineProps<{ light?: boolean }>()
</script>

<template>
  <div class="ine-wordmark" :class="{ 'ine-wordmark--light': light }">
    <span class="ine-wordmark__name">INESDI</span>
    <span class="ine-wordmark__tag">Business<br />Techschool</span>
  </div>
</template>

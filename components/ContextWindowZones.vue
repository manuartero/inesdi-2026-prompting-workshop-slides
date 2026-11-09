<script setup lang="ts">
withDefaults(defineProps<{ sharpRatio?: number }>(), { sharpRatio: 0.4 })
</script>

<template>
  <div class="zones">
    <div class="zones__bar">
      <div class="zones__half zones__half--sharp" :style="{ flexBasis: `${sharpRatio * 100}%` }">Zona lúcida</div>
      <div class="zones__half zones__half--fuzzy" :style="{ flexBasis: `${(1 - sharpRatio) * 100}%` }">Zona torpe</div>
    </div>
    <div class="zones__caption">la conversación entera (la «ventana de contexto») →</div>
  </div>
</template>

<style scoped>
.zones {
  width: min(720px, 92%);
  margin: 0 auto;
}
.zones__bar {
  display: flex;
  height: 3.4rem;
  border: 1px solid var(--ine-ink);
}
.zones__half {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1rem;
  font-weight: 500;
}
.zones__half--sharp {
  background: var(--ine-ink);
  color: white;
}
.zones__half--fuzzy {
  background: repeating-linear-gradient(-45deg, var(--ine-line), var(--ine-line) 1px, transparent 1px, transparent 8px);
  color: var(--ine-muted);
}
.zones__caption {
  margin-top: 0.4rem;
  font-size: 0.75rem;
  color: var(--ine-muted);
}
</style>

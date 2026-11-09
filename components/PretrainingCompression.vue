<template>
  <div class="ptc">
    <div class="ptc__big"><b>10 TB</b> <span>de textos</span></div>
    <span class="ptc__note">casi todo lo publicado en internet</span>
    <svg class="ptc__arrow" viewBox="0 0 24 60" fill="none" aria-hidden="true">
      <line x1="12" y1="4" x2="12" y2="48" stroke="currentColor" stroke-width="3" stroke-linecap="round" />
      <polyline points="4,40 12,52 20,40" stroke="currentColor" stroke-width="3" stroke-linecap="round" stroke-linejoin="round" />
    </svg>
    <div class="ptc__heading">Entrenamiento</div>
    <p class="ptc__desc">lo comprime en un fichero de números mucho más pequeño</p>
    <svg class="ptc__arrow" viewBox="0 0 24 60" fill="none" aria-hidden="true">
      <line x1="12" y1="4" x2="12" y2="48" stroke="currentColor" stroke-width="3" stroke-linecap="round" />
      <polyline points="4,40 12,52 20,40" stroke="currentColor" stroke-width="3" stroke-linecap="round" stroke-linejoin="round" />
    </svg>
    <div class="ptc__big"><b>140 GB</b> <span>de parámetros</span></div>
    <span class="ptc__note">el modelo</span>
  </div>
</template>

<style scoped>
.ptc {
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}
.ptc__big {
  font-size: 1.6rem;
  line-height: 1.1;
}
.ptc__big b {
  font-weight: 700;
}
.ptc__big span {
  color: var(--ine-muted);
}
.ptc__note {
  font-size: 0.75rem;
  color: var(--ine-muted);
}
.ptc__heading {
  font-size: 1.2rem;
  font-weight: 600;
  color: var(--ine-ink);
}
.ptc__desc {
  margin: 0 !important;
  font-size: 0.8rem;
  color: var(--ine-muted);
  max-width: 18rem;
}
.ptc__arrow {
  width: 20px;
  height: 40px;
  color: var(--ine-ink);
  margin: 0.2rem 0;
}
</style>

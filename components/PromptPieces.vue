<script setup lang="ts">
// The demo's prompt B, one piece per click: the active piece opens, the rest stay folded.
// Slide content (Spanish) lives here so the slide stays a one-liner.
const props = defineProps<{ active: number }>()

interface Piece {
  name: string
  tag: string
  icon: string
  lines: string[]
}

const pieces: Piece[] = [
  {
    name: 'Adjunto',
    tag: '📎',
    icon: 'i-ph-paperclip-fill',
    lines: ['peluda-tickets-hoy.csv (exportado del CMS)'],
  },
  {
    name: 'Rol',
    tag: '<rol>',
    icon: 'i-ph-identification-badge-fill',
    lines: ['Responsable del equipo de atención al cliente de Peluda'],
  },
  {
    name: 'Contexto',
    tag: '<contexto>',
    icon: 'i-ph-buildings-fill',
    lines: [
      'Peluda vende comida para mascotas por suscripción: cada 4 semanas enviamos un pedido a casa. Hay tres planes: Básico, Completo y Cuidado.',
      'Hace unas semanas cambiamos la receta del pienso de perro adulto en España.',
    ],
  },
  {
    name: 'Goal',
    tag: '<goal>',
    icon: 'i-ph-target-fill',
    lines: ['Clasifica los tickets por categoría y urgencia.'],
  },
  {
    name: 'Formato',
    tag: '<formato>',
    icon: 'i-ph-table-fill',
    lines: [
      '1. Tabla con los 15 tickets más urgentes: ID | Categoría | Urgencia | Resumen | Por qué urgente.',
      '2. Tabla con cuántos tickets hay de cada categoría y de cada urgencia.',
      '3. Si varios tickets hablan del mismo problema, cuáles son y qué tienen en común.',
      'Categorías: Envío, Facturación, Cambio de plan, Baja, Salud de la mascota, Cuenta, Otro.',
      'Urgencia Alta: salud de una mascota, mascota sin comida, cobro indebido o amenaza…',
    ],
  },
  {
    name: 'Restricciones',
    tag: '<restricciones>',
    icon: 'i-ph-prohibit-fill',
    lines: [
      '- Lee todos los tickets del fichero.',
      '- Si un ticket trata dos asuntos, clasifícalo por el más grave.',
      '- No inventes nada. Si no puedes decidir, escribe «Revisar».',
    ],
  },
]

const isOpen = (index: number) => props.active === index + 1
const isPending = (index: number) => props.active > 0 && index + 1 > props.active
</script>

<template>
  <div class="pieces">
    <div
      v-for="(piece, index) in pieces"
      :key="piece.name"
      class="piece"
      :class="{ 'piece--open': isOpen(index), 'piece--pending': isPending(index) }"
    >
      <div class="piece__head">
        <span class="piece__icon"><span :class="piece.icon" /></span>
        <span class="piece__label">
          <b class="piece__name">{{ piece.name }}</b>
          <code class="piece__tag">{{ piece.tag }}</code>
        </span>
        <span class="piece__preview">{{ piece.lines[0] }}</span>
      </div>
      <div class="piece__body">
        <div>
          <p v-for="line in piece.lines" :key="line">{{ line }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.pieces {
  display: flex;
  flex-direction: column;
  gap: 0.35rem;
}
.piece {
  border: 1.5px solid var(--ine-line);
  background: white;
  padding: 0.3rem 0.8rem;
  transition: opacity 0.3s, border-color 0.3s;
}
.piece--open {
  border-color: var(--ine-yellow);
  box-shadow: inset 4px 0 0 var(--ine-yellow);
}
.piece--pending {
  opacity: 0.4;
}
.piece__head {
  display: grid;
  grid-template-columns: auto 15rem 1fr;
  align-items: center;
  gap: 0.6rem;
  font-size: 0.85rem;
}
.piece__icon {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 1.7rem;
  height: 1.7rem;
  border-radius: 9999px;
  background: var(--ine-yellow);
  font-size: 0.95rem;
}
.piece__label {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}
.piece__name {
  font-weight: 600;
}
.piece__tag {
  font-size: 0.7rem;
  background: var(--ine-soft);
  padding: 0.1rem 0.35rem;
  justify-self: start;
}
.piece__preview {
  font-size: 0.75rem;
  color: var(--ine-muted);
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  transition: opacity 0.2s;
}
.piece--open .piece__preview {
  opacity: 0;
}
.piece__body {
  display: grid;
  grid-template-rows: 0fr;
  transition: grid-template-rows 0.35s ease;
}
.piece__body > div {
  overflow: hidden;
  padding-left: 2.3rem;
}
.piece--open .piece__body {
  grid-template-rows: 1fr;
}
.piece__body p {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.68rem;
  line-height: 1.5;
  margin: 0;
}
.piece__body p:first-child {
  margin-top: 0.4rem;
}
</style>

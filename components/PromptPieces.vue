<script setup lang="ts">
// The demo's prompt B in two columns: the six pieces on the left, the prompt on the right.
// Each click selects a piece; the prompt scrolls to it and highlights its lines.
// Slide content (Spanish) lives here so the slide stays a one-liner.
import { nextTick, ref, watch } from 'vue'

const props = defineProps<{ active: number }>()

type PieceKey = 'attachment' | 'role' | 'context' | 'goal' | 'format' | 'constraints'

interface Piece {
  key: PieceKey
  name: string
  tag: string
  icon: string
}

const pieces: Piece[] = [
  { key: 'attachment', name: 'Adjunto', tag: '📎', icon: 'i-ph-paperclip-fill' },
  { key: 'role', name: 'Rol', tag: '<rol>', icon: 'i-ph-identification-badge-fill' },
  { key: 'context', name: 'Contexto', tag: '<contexto>', icon: 'i-ph-buildings-fill' },
  { key: 'goal', name: 'Goal', tag: '<goal>', icon: 'i-ph-target-fill' },
  { key: 'format', name: 'Formato', tag: '<formato>', icon: 'i-ph-table-fill' },
  { key: 'constraints', name: 'Restricciones', tag: '<restricciones>', icon: 'i-ph-prohibit-fill' },
]

// The prompt as typed in the chat, line by line, each line tagged with its piece.
const promptLines: { text: string; piece?: PieceKey }[] = [
  { text: '📎 peluda-tickets-hoy.csv', piece: 'attachment' },
  { text: '' },
  { text: '<rol>Responsable del equipo de atención al cliente de Peluda</rol>', piece: 'role' },
  { text: '' },
  { text: '<contexto>', piece: 'context' },
  { text: 'Peluda vende comida para mascotas por suscripción: cada 4 semanas enviamos un pedido a casa. Hay tres planes: Básico, Completo y Cuidado.', piece: 'context' },
  { text: 'Hace unas semanas cambiamos la receta del pienso de perro adulto en España.', piece: 'context' },
  { text: 'Adjunto bandeja de tickets (CSV, un ticket por fila).', piece: 'attachment' },
  { text: '</contexto>', piece: 'context' },
  { text: '' },
  { text: '<goal>Clasifica los tickets por categoría y urgencia.</goal>', piece: 'goal' },
  { text: '' },
  { text: '<formato>', piece: 'format' },
  { text: '1. Tabla con los 15 tickets más urgentes, de más a menos: ID | Categoría | Urgencia | Resumen | Por qué urgente.', piece: 'format' },
  { text: '2. Tabla con cuántos tickets hay de cada categoría y de cada urgencia.', piece: 'format' },
  { text: '3. Una o dos líneas: si varios tickets hablan del mismo problema, cuáles son y qué tienen en común.', piece: 'format' },
  { text: '', piece: 'format' },
  { text: 'Categorías: Envío, Facturación, Cambio de plan, Baja, Salud de la mascota, Cuenta, Otro.', piece: 'format' },
  { text: 'Urgencia:', piece: 'format' },
  { text: '- Alta: salud de una mascota, mascota sin comida, cobro indebido o amenaza.', piece: 'format' },
  { text: '- Media: un problema real que puede esperar a mañana.', piece: 'format' },
  { text: '- Baja: consultas y gestiones.', piece: 'format' },
  { text: '</formato>', piece: 'format' },
  { text: '' },
  { text: '<restricciones>', piece: 'constraints' },
  { text: '- Lee todos los tickets del fichero.', piece: 'constraints' },
  { text: '- Si un ticket trata dos asuntos, clasifícalo por el más grave.', piece: 'constraints' },
  { text: '- No inventes nada que no esté en el ticket. Si no puedes decidir, escribe «Revisar».', piece: 'constraints' },
  { text: '</restricciones>', piece: 'constraints' },
]

const activePiece = () => pieces[props.active - 1]?.key

const isActive = (index: number) => props.active === index + 1
const isPending = (index: number) => props.active > 0 && index + 1 > props.active
const lineState = (piece?: PieceKey) => {
  const active = activePiece()
  if (!active) return ''
  return piece === active ? 'line--on' : 'line--off'
}

// Scroll the prompt so the active piece's first line sits near the top of the window.
const windowEl = ref<HTMLElement>()
const lineEls = ref<HTMLElement[]>([])
const offset = ref(0)

const TOP_MARGIN_PX = 16

watch(
  () => props.active,
  async () => {
    await nextTick()
    const active = activePiece()
    const first = promptLines.findIndex((line) => line.piece === active)
    const lineEl = lineEls.value[first]
    const viewport = windowEl.value
    if (!active || !lineEl || !viewport) {
      offset.value = 0
      return
    }
    const content = viewport.firstElementChild as HTMLElement
    const maxOffset = Math.max(0, content.offsetHeight - viewport.clientHeight)
    offset.value = Math.min(Math.max(0, lineEl.offsetTop - TOP_MARGIN_PX), maxOffset)
  },
  { immediate: true },
)
</script>

<template>
  <div class="prompt-pieces">
    <ol class="pieces">
      <li
        v-for="(piece, index) in pieces"
        :key="piece.key"
        class="piece"
        :class="{ 'piece--active': isActive(index), 'piece--pending': isPending(index) }"
      >
        <span class="piece__icon"><span :class="piece.icon" /></span>
        <b class="piece__name">{{ piece.name }}</b>
        <code class="piece__tag">{{ piece.tag }}</code>
      </li>
    </ol>

    <div ref="windowEl" class="prompt">
      <div class="prompt__content" :style="{ transform: `translateY(-${offset}px)` }">
        <p
          v-for="(line, index) in promptLines"
          :key="index"
          ref="lineEls"
          class="line"
          :class="lineState(line.piece)"
        >{{ line.text || ' ' }}</p>
      </div>
    </div>
  </div>
</template>

<style scoped>
.prompt-pieces {
  display: grid;
  grid-template-columns: 16.5rem 1fr;
  gap: 1.5rem;
  align-items: start;
}

.pieces {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 0.4rem;
}
.piece {
  display: flex;
  align-items: center;
  gap: 0.55rem;
  padding: 0.4rem 0.6rem;
  margin: 0;
  background: white;
  border: 1.5px solid var(--ine-line);
  font-size: 0.85rem;
  transition: opacity 0.3s, border-color 0.3s;
}
.piece::before {
  content: none !important;
}
.piece--active {
  border-color: var(--ine-yellow);
  box-shadow: inset 4px 0 0 var(--ine-yellow);
}
.piece--pending {
  opacity: 0.4;
}
.piece__icon {
  flex: none;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 1.7rem;
  height: 1.7rem;
  border-radius: 9999px;
  background: var(--ine-yellow);
  font-size: 0.95rem;
}
.piece__name {
  font-weight: 600;
}
.piece__tag {
  margin-left: auto;
  font-size: 0.62rem;
  padding: 0.05rem 0.3rem;
}

.prompt {
  height: 330px;
  overflow: hidden;
  background: white;
  border: 1.5px solid var(--ine-line);
  position: relative;
}
.prompt::after {
  content: '';
  position: absolute;
  inset: auto 0 0 0;
  height: 2rem;
  background: linear-gradient(transparent, white);
  pointer-events: none;
}
.prompt__content {
  padding: 0.8rem 1rem 1.8rem;
  transition: transform 0.5s ease;
}
.line {
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.66rem;
  line-height: 1.55;
  margin: 0;
  padding: 0 0.3rem;
  transition: opacity 0.3s, background-color 0.3s;
}
.line--on {
  background: color-mix(in srgb, var(--ine-yellow) 28%, white);
}
.line--off {
  opacity: 0.3;
}
</style>

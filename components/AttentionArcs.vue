<script setup lang="ts">
import { computed } from 'vue'

const props = withDefaults(
  defineProps<{ words?: string[]; showLastWord?: boolean; showArcs?: boolean }>(),
  {
    words: () => ['mi', 'perro', 'vomita', 'desde', 'que', 'cambió', 'el', 'pienso'],
    showLastWord: true,
    showArcs: true,
  },
)

const VIEW_W = 800
const VIEW_H = 260
const BOX_W = 86
const BOX_H = 38
const BOX_Y = 200
const PAD_X = 50

const positions = computed(() => {
  const span = VIEW_W - PAD_X * 2
  return props.words.map((_, index) => PAD_X + (span * index) / (props.words.length - 1))
})

const arcs = computed(() => {
  const top = BOX_Y - 2
  const lastIndex = props.words.length - 1
  return props.words.flatMap((_, from) =>
    props.words.slice(from + 1).map((__, offset) => {
      const to = from + 1 + offset
      const [x1, x2] = [positions.value[from], positions.value[to]]
      const apex = top - (24 + (to - from) * 22)
      return {
        key: `${from}-${to}`,
        d: `M ${x1} ${top} Q ${(x1 + x2) / 2} ${apex} ${x2} ${top}`,
        isNew: to === lastIndex,
      }
    }),
  )
})
</script>

<template>
  <svg class="arcs" :viewBox="`0 0 ${VIEW_W} ${VIEW_H}`" preserveAspectRatio="xMidYMid meet">
    <g v-if="showArcs">
      <path
        v-for="arc in arcs"
        :key="arc.key"
        :d="arc.d"
        fill="none"
        :stroke="arc.isNew ? 'var(--ine-ink)' : 'var(--ine-ink)'"
        :stroke-width="arc.isNew ? 2.2 : 1"
        :stroke-opacity="arc.isNew ? 1 : 0.25"
        stroke-linecap="round"
      />
    </g>
    <g
      v-for="(word, index) in words"
      :key="index"
      :transform="`translate(${positions[index] - BOX_W / 2} ${BOX_Y})`"
      :visibility="index === words.length - 1 && !showLastWord ? 'hidden' : 'visible'"
    >
      <rect
        :width="BOX_W"
        :height="BOX_H"
        :fill="index === words.length - 1 ? 'var(--ine-yellow)' : 'var(--ine-paper)'"
        stroke="var(--ine-ink)"
        stroke-width="1"
      />
      <text :x="BOX_W / 2" :y="BOX_H / 2 + 6" text-anchor="middle" class="arcs__label">{{ word }}</text>
    </g>
  </svg>
</template>

<style scoped>
.arcs {
  width: 100%;
  max-width: 820px;
  display: block;
  margin: 0 auto;
}
.arcs__label {
  font-size: 17px;
  font-weight: 500;
  fill: var(--ine-ink);
}
</style>

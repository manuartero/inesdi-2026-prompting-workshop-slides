<script setup lang="ts">
const BOX_W = 116
const BOX_H = 44
const GAP = 12
const SVG_W = 740
const START_X = (SVG_W - (5 * BOX_W + 4 * GAP)) / 2
const BOX_Y = 16
const CENTER_Y = BOX_Y + BOX_H / 2
const LOOP_Y = 116

const stages = ['Negación', 'Enfado', 'Negociación', 'Desánimo', 'Aceptación'].map((name, index) => ({
  name,
  x: START_X + index * (BOX_W + GAP),
}))
const last = stages[stages.length - 1]
const loopPath = `M ${last.x + BOX_W} ${CENTER_Y} C 712 ${CENTER_Y} 712 ${LOOP_Y} 370 ${LOOP_Y} C 28 ${LOOP_Y} 28 ${CENTER_Y} ${stages[0].x} ${CENTER_Y}`
</script>

<template>
  <svg :viewBox="`0 0 ${SVG_W} 140`" class="grief" aria-hidden="true">
    <defs>
      <marker id="grief-arrow" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="6" markerHeight="6" orient="auto">
        <path d="M 0 0 L 10 5 L 0 10 z" fill="var(--ine-navy)" />
      </marker>
    </defs>
    <g v-for="(stage, index) in stages" :key="stage.name">
      <rect
        :x="stage.x"
        :y="BOX_Y"
        :width="BOX_W"
        :height="BOX_H"
        :fill="index === stages.length - 1 ? 'var(--ine-yellow)' : 'white'"
        stroke="var(--ine-ink)"
        stroke-width="1.5"
      />
      <text :x="stage.x + BOX_W / 2" :y="CENTER_Y + 5" class="grief__name">{{ stage.name }}</text>
      <line
        v-if="index > 0"
        :x1="stages[index - 1].x + BOX_W + 2"
        :y1="CENTER_Y"
        :x2="stage.x - 3"
        :y2="CENTER_Y"
        stroke="var(--ine-ink)"
        stroke-width="1.5"
        marker-end="url(#grief-arrow)"
      />
    </g>
    <path :d="loopPath" fill="none" stroke="var(--ine-navy)" stroke-width="2" stroke-dasharray="6 3" marker-end="url(#grief-arrow)" />
    <text x="370" y="134" class="grief__loop">cada vuelta es más corta y menos intensa</text>
  </svg>
</template>

<style scoped>
.grief {
  display: block;
  width: 100%;
  height: auto;
}
.grief__name {
  font-size: 13px;
  font-weight: 600;
  text-anchor: middle;
  fill: var(--ine-ink);
}
.grief__loop {
  font-size: 11px;
  text-anchor: middle;
  fill: var(--ine-navy);
}
</style>

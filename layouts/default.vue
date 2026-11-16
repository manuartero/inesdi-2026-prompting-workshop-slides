<script setup lang="ts">
import { computed } from 'vue'
import { useSlideContext } from '@slidev/client'

const { $slidev, $page, $nav } = useSlideContext()

// The kicker names the section this slide belongs to: the nearest section slide before it,
// shown only when that section slide sets `kicker` in its frontmatter.
const kicker = computed(() => {
  const slides = $nav.value.slides
  for (let index = $page.value - 2; index >= 0; index--) {
    const frontmatter = slides[index]?.meta?.slide?.frontmatter
    if (frontmatter?.layout === 'section')
      return frontmatter.kicker ? { number: frontmatter.number, name: frontmatter.kicker } : undefined
  }
  return undefined
})
</script>

<template>
  <div class="slidev-layout ine-light ine-default">
    <div class="ine-default__body">
      <p v-if="kicker" class="ine-kicker"><span v-if="kicker.number" class="ine-kicker__number">{{ kicker.number }}</span>{{ kicker.name }}</p>
      <slot />
    </div>
    <footer class="ine-footer">
      <span>{{ $slidev.configs.title }}</span>
      <span>
        {{ $slidev.nav.currentPage }}
      </span>
    </footer>
  </div>
</template>

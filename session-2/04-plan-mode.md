---
layout: section
number: '04'
kicker: 'Plan mode'
---

# Plan mode

Primero el plan, después la implementación

---

# Corregir un plan cuesta una frase

<div class="grid grid-cols-[1.3fr_1fr] gap-8 mt-2">
<div>

<div class="ine-tile ine-tile--accent">
  <span class="ine-tile__icon"><span class="i-ph-list-checks-fill" /></span>
  <h3>La frase</h3>
  <p class="text-base">«<b>No hagas nada todavía.</b> Dame el plan: qué vas a hacer, en qué orden y qué necesitas de mí. Espera mi OK.»</p>
</div>

<p class="text-sm mt-4">Corregir el resultado cuesta rehacerlo.</p>

</div>
<div class="ine-card">

### Así se hicieron estas slides

<p class="text-sm"><b>1 ·</b> «Plan mode first»: me propuso un plan.</p>
<p class="text-sm mt-1"><b>2 ·</b> Le dije: «más reducida».</p>
<p class="text-sm mt-1"><b>3 ·</b> Corrigió el plan <b>antes de tocar nada</b>.</p>

<p class="text-xs mt-2" style="color: var(--ine-muted)">En Claude Code es un modo. En el chat no hay botón: se pide con la frase.</p>

</div>
</div>

<!--
Grill me y plan mode son el mismo gesto: que te ayude a pensar antes de hacer el trabajo. En grill me te pregunta; en plan mode te propone y tú decides.
La anécdota es real: esta sesión se preparó así con Claude Code. El plan proponía unas 30 slides; «más reducida»; el plan cambió antes de escribir una sola.
-->

---

# Demo: un prompt para preparar el prompt

<div class="grid grid-cols-[1.4fr_1fr] gap-8 mt-2">
<div>

```text
[pega la guía de voz de Peluda]

Quiero un prompt para responder reseñas
de clientes siguiendo esta guía.

No lo escribas todavía. Dame primero el
plan: qué partes tendrá y qué te falta
saber. Cuando te dé el OK, escríbelo.
```

</div>
<div class="topic-list">
  <TopicRow title="1 · El plan" icon="i-ph-list-checks-fill">rol, guía, ejemplos, formato…</TopicRow>
  <TopicRow title="2 · Tú corriges" icon="i-ph-pencil-simple-fill">«y que nunca repita datos personales»</TopicRow>
  <TopicRow title="3 · El prompt" tone="warning" icon="i-ph-magic-wand-fill">lo escribe él: <b>meta-prompting</b></TopicRow>
</div>
</div>

<p class="text-sm mt-4" style="color: var(--ine-muted)">La guía de voz, en el CMS: <b>Marca</b> → «Copiar para el prompt».</p>

<!--
Meta-prompting: un prompt cuyo resultado es otro prompt. Útil para empezar; el prompt que te da también hay que probarlo.
Qué corregir en el plan si no lo trae: no repetir datos personales; salud → veterinario en la primera frase; no prometer nada que no se pueda comprobar; analizar la reseña antes de responder.
Prompts en demos/sesion-2/03-plan-mode.md.
-->

---

# Tu turno: pruébalo con dos reseñas

<div class="grid grid-cols-2 gap-6 mt-2">
<div class="ine-tile">
  <span class="ine-tile__icon"><span class="i-ph-first-aid-kit-fill" /></span>
  <h3>Rocío · 2 estrellas</h3>
  <p class="ine-tile__example">«Desde que cambiaron el pienso mi perra vomita casi todos los días. Antes estaba perfecta. Ya la he llevado al veterinario. ¿A alguien más le pasa?»</p>
  <p class="ine-tile__remedy">Veterinario en la primera frase, el lote por privado, <b>sin diagnosticar</b>.</p>
</div>
<div class="ine-tile">
  <span class="ine-tile__icon"><span class="i-ph-identification-card-fill" /></span>
  <h3>Patricia · 2 estrellas · México</h3>
  <p class="ine-tile__example">«Me llegaron las croquetas del gato. Me cobraron con mi tarjeta terminación 4417. Llámenme al +52 222… o vengan a Calle 5 de Mayo…»</p>
  <p class="ine-tile__remedy">Ni tarjeta, ni teléfono, ni dirección: <b>a un canal privado</b>.</p>
</div>
</div>

<p class="mt-4">En el CMS: <b>Reseñas</b> → «Copiar para el prompt». Pega en el chat de la clase <b>la respuesta que publicarías</b>.</p>

<!--
Rocío: cierra el hilo del perro que vomita (tickets 0004, 0015, 0063, 0145 y la cláusula 5.4 de NutriCan: 48 horas). Responder bien la reseña no basta: alguien tiene que avisar a Producto y al fabricante.
Patricia: México → tú, cálido y algo más formal. El fallo típico es repetir el teléfono o la dirección «para confirmar». Además, pedir que se oculte la reseña.
Antes de publicar, una persona revisa: nombre y trato; salud sin diagnóstico; ningún dato personal repetido; nada prometido que no podamos cumplir; ¿hay que avisar a alguien?; ¿la firmarías tú?
-->

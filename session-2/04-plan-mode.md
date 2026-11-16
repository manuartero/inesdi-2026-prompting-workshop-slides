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
  <TopicRow title="2 · Tú corriges" icon="i-ph-pencil-simple-fill">contestas y añades: «nunca repitas datos personales»</TopicRow>
  <TopicRow title="3 · El prompt" tone="warning" icon="i-ph-magic-wand-fill">lo escribe él: <b>meta-prompting</b></TopicRow>
</div>
</div>

<p class="text-sm mt-4" style="color: var(--ine-muted)">La guía de voz, en el CMS: <b>Marca</b> → «Copiar para el prompt».</p>

<!--
Meta-prompting: un prompt cuyo resultado es otro prompt. Útil para empezar; el prompt que te da también hay que probarlo.
Prompts, respuestas y resultado en demos/sesion-2/03-plan-mode.md.
-->

---

# El plan, y el prompt

<div class="grid grid-cols-2 gap-8">
<div>

## 1 · El plan

<div class="relative inline-block mt-1">
  <img src="/captures/s2-plan-mode-plan.png" style="height: 212px" class="border border-gray-300" alt="El plan: siete partes y nueve preguntas antes de escribir" />
  <span class="ine-hl" style="left: 4%; top: 30.8%; width: 88%; height: 5%" />
  <span class="ine-hl" style="left: 4%; top: 52.4%; width: 30%; height: 2.8%" />
</div>

<p class="mt-2" style="font-size: 0.8rem; line-height: 1.4">7 partes y <b>9 preguntas</b>. Y por su cuenta: en salud, el veterinario va <b>antes que el perdón</b>.</p>

</div>
<div>

## 3 · El prompt

<div class="relative inline-block mt-1">
  <img src="/captures/s2-plan-mode-prompt.png" style="height: 212px" class="border border-gray-300" alt="El prompt final, escrito por el modelo" />
  <span class="ine-hl" style="left: 6%; top: 46.2%; width: 88%; height: 2.6%" />
</div>

<p class="mt-2" style="font-size: 0.8rem; line-height: 1.4">150 líneas con 4 ejemplos, que no escribirías a mano. <b>Lo guardamos: será una skill.</b></p>

</div>
</div>

<style>
.ine-hl {
  position: absolute;
  background: rgba(255, 192, 0, 0.3);
  border-bottom: 2px solid var(--ine-yellow);
}
</style>

<!--
Resultado real (16/11).
El plan: rol y voz, datos de entrada, pasos antes de escribir, reglas, qué puede prometer y qué no, formato de salida (respuesta + nota para quien revisa) y ejemplos. Y 9 preguntas: dónde se usa, plataformas, qué datos tendrá, compromisos, trolls repetidos, idiomas, país desconocido, precios en Argentina, firma.
Dos cosas que hizo sin que se lo pidiéramos: fijar que en salud el veterinario va antes que el perdón (la guía no lo ordena) y proteger contra inventar: todo importe o plazo va entre corchetes.
Contestamos las 9 en un mensaje, añadimos «nunca repitas datos personales» y dimos el OK. Corregir el plan costó un mensaje.
El prompt final es la skill peluda-resenas del bloque siguiente, tal cual.
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

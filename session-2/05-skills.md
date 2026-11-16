---
layout: section
kicker: "Skills"
number: '05'
---

# Skills

Prompts preparados y compartidos

---

# ¿Os suena?

<div class="grid grid-cols-[1.3fr_1fr] gap-8 mt-2">
<div>

```text
<contexto>
Peluda vende comida para mascotas por
suscripción: cada 4 semanas enviamos un
pedido a casa. Hay tres planes: Básico,
Completo y Cuidado.
Hace unas semanas cambiamos la receta del
pienso de perro adulto en España.
</contexto>
```

<p class="text-xs mt-2" style="color: var(--ine-muted)">El prompt de la demo de la sesión 1.</p>

</div>
<div class="flex flex-col gap-4">
<div class="ine-tile ine-tile--muted">
  <span class="ine-tile__icon"><span class="i-ph-repeat-fill" /></span>
  <h3>Lo escribimos en cada prompt</h3>
  <p>Y cada persona del equipo, a su manera.</p>
</div>
<div class="ine-tile ine-tile--accent">
  <span class="ine-tile__icon"><span class="i-ph-package-fill" /></span>
  <h3>¿Y si ya estuviera escrito?</h3>
  <p>Una vez, bien hecho, y para todo el equipo.</p>
</div>
</div>
</div>

---

# Una skill no es más que un .md

<div class="grid grid-cols-[1.4fr_1fr] gap-8 mt-2">
<div>

```text
---
name: peluda-contexto
description: Quién es Peluda, qué vende y
  cómo funciona. Úsala en cualquier tarea
  de Peluda antes de responder.
---

Trabajas para Peluda, una empresa de comida
para perros y gatos por suscripción…

- Tres planes: Básico, Completo y Cuidado.
- España, México, Perú, Colombia y Argentina.
- Si te falta un dato de Peluda, pregúntalo.
```

</div>
<div class="topic-list">
  <TopicRow title="Nombre" icon="i-ph-tag-fill">para encontrarla</TopicRow>
  <TopicRow title="Descripción" icon="i-ph-signpost-fill">cuándo usarla: el modelo la lee y decide</TopicRow>
  <TopicRow title="Instrucciones" icon="i-ph-text-align-left-fill">el prompt de siempre, escrito una vez</TopicRow>
  <TopicRow title="Se comparte" tone="warning" icon="i-ph-users-three-fill">un fichero: se pasa al equipo y se mejora</TopicRow>
</div>
</div>

<p class="text-sm mt-4" style="color: var(--ine-muted)">En Claude se llaman Skills. En ChatGPT y Gemini, la misma idea con otro nombre: GPT, Gems, Proyectos.</p>

<!--
Lo importante es la idea, no el botón: un texto preparado que se reutiliza y se comparte. Si tu herramienta no tiene Skills, pega el .md al principio del chat o en las instrucciones de un Proyecto: es lo mismo.
La descripción es la parte que más se descuida y la que más importa: con ella decide el modelo si la usa.
-->

---

# Demo: dos skills y una reseña

<div class="grid grid-cols-[1fr_1.2fr] gap-8 mt-2">
<div class="flex flex-col gap-4">
<div class="ine-tile">
  <span class="ine-tile__icon"><span class="i-ph-buildings-fill" /></span>
  <h3>peluda-contexto.md</h3>
  <p>Quiénes somos: planes, países, proveedores. Sirve para cualquier tarea.</p>
</div>
<div class="ine-tile">
  <span class="ine-tile__icon"><span class="i-ph-star-fill" /></span>
  <h3>peluda-resenas.md</h3>
  <p>El prompt que salió del plan mode + la guía de voz entera.</p>
</div>
</div>
<div>

## Y el chat, entero

```text
Responde a esta reseña:

«Me llegaron las croquetas del gato.
Me cobraron con mi tarjeta terminación
4417. Llámenme al +52 222…»
```

<p class="mt-4">El prompt largo ya no se escribe. <b>Se escribe la tarea.</b></p>

<div class="ine-todo mt-4">TODO: captura de la respuesta (s2-skill.png)</div>

</div>
</div>

<!--
Es la reseña de Patricia, que ya probaron en plan mode con el prompt entero. Mismo resultado (o mejor), con una línea.
Lo que hay que ver en la respuesta: análisis → respuesta → avisos; trato de tú cálido (México); no repite la tarjeta ni el teléfono; pide pasar a privado y ocultar la reseña.
Montaje y prompts en demos/sesion-2/04-skill.md.
-->

---

# Tu turno: con las skills

<div class="grid grid-cols-[1.3fr_1fr] gap-8 mt-2">
<div class="grid grid-cols-2 gap-4">
<div class="ine-tile">
  <span class="ine-tile__icon"><span class="i-ph-smiley-angry-fill" /></span>
  <h3>Kike_88 · 1 estrella</h3>
  <p class="ine-tile__example">«Pienso del súper metido en una bolsa bonita y a 45 pavos. Una estafa para pijos…»</p>
</div>
<div class="ine-tile">
  <span class="ine-tile__icon"><span class="i-ph-heart-fill" /></span>
  <h3>Pilar · 5 estrellas</h3>
  <p class="ine-tile__example">«Nala nos dejó con 16 años. Comió Peluda desde el primer mes… Gracias a todo el equipo.»</p>
</div>
</div>
<div class="topic-list">
  <TopicRow title="1" icon="i-ph-download-simple-fill">descarga las dos skills</TopicRow>
  <TopicRow title="2" icon="i-ph-upload-simple-fill">súbelas, o pégalas al principio del chat</TopicRow>
  <TopicRow title="3" icon="i-ph-chat-circle-text-fill">«Responde a esta reseña:» + la reseña</TopicRow>
  <TopicRow title="4" icon="i-ph-paper-plane-tilt-fill">pega en el chat de la clase la que publicarías</TopicRow>
</div>
</div>

<div class="flex justify-center gap-8 mt-6 text-sm font-semibold">
  <a href="https://inesdi-2026-prompting-workshop-slid.vercel.app/session-2/skills/peluda-contexto.md" class="inline-flex items-center gap-2 !border-none"><ph-file-text-fill class="text-xl" /> peluda-contexto.md</a>
  <a href="https://inesdi-2026-prompting-workshop-slid.vercel.app/session-2/skills/peluda-resenas.md" class="inline-flex items-center gap-2 !border-none"><ph-file-text-fill class="text-xl" /> peluda-resenas.md</a>
</div>

<!--
Kike (troll): una sola respuesta, breve y educada, sin entrar al trapo. Fallo típico: un argumentario a la defensiva (ingredientes, precio por día…).
Pilar: cinco estrellas, pero es un duelo. Respetuosa, sin emojis, sin vender nada y confirmando que no habrá más envíos ni cobros (va con el ticket 0024).
Las reseñas, en el CMS: Reseñas → «Copiar para el prompt».
-->

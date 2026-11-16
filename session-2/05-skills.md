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
name: peluda-review
description: Redacta borradores de respuesta a
  reseñas de clientes de Peluda con la voz de
  la marca. Úsala cuando te pidan responder
  a una reseña.
---

Eres quien redacta borradores de respuesta a
reseñas de clientes de Peluda…

# Voz
# Antes de escribir
# Reglas · Datos personales · Firma…
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

# Demo: una skill y una reseña

<div class="grid grid-cols-[1fr_1.2fr] gap-8 mt-2">
<div>
<div class="ine-tile ine-tile--accent">
  <span class="ine-tile__icon"><span class="i-ph-star-fill" /></span>
  <h3>peluda-review.md</h3>
  <p>El prompt que escribió el modelo en plan mode, <b>tal cual</b>. La guía de voz ya va dentro.</p>
</div>
<p class="mt-4 text-sm font-semibold"><a href="https://inesdi-2026-prompting-workshop-slid.vercel.app/session-2/skills/peluda-review.zip" class="inline-flex items-center gap-2 !border-none"><ph-file-zip-fill class="text-xl" /> Descargar peluda-review.zip</a></p>
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
Es la reseña de Patricia, que ya probaron en plan mode con el prompt entero. Mismo resultado, con una línea.
Lo que hay que ver en la respuesta: RESPUESTA + NOTA PARA QUIEN REVISA; trato de tú cálido (México); no repite la tarjeta ni el teléfono; pide pasar a privado; en la nota, alerta de datos personales.
Montaje y prompts en demos/sesion-2/04-skill.md.
-->

---

# Tu turno: tu primera skill

<div class="grid grid-cols-[1.2fr_1fr] gap-8 mt-2">
<div>

```text
---
name: peluda-context
description: Quién es Peluda, qué vende y
  cómo funciona. Úsala en cualquier tarea
  de Peluda antes de responder.
---

## Qué vendemos      → el <contexto> de la sesión 1
## Los planes        → CMS · Clientes
## Dónde estamos     → CMS · Inicio
## Lo que pasa ahora → el <contexto> de la sesión 1
## Reglas            → ya vienen dos
```

</div>
<div class="topic-list">
  <TopicRow title="1" icon="i-ph-download-simple-fill">descarga la plantilla: cada hueco lleva su pista</TopicRow>
  <TopicRow title="2" icon="i-ph-pencil-simple-fill">rellena los huecos: cinco líneas, ninguna difícil</TopicRow>
  <TopicRow title="3" icon="i-ph-upload-simple-fill">súbela junto a peluda-review, o pega las dos al principio del chat</TopicRow>
  <TopicRow title="4" icon="i-ph-chat-circle-text-fill">«Responde a esta reseña:» + la de Kike o la de Pilar</TopicRow>
</div>
</div>

<div class="flex justify-center gap-8 mt-4 text-sm font-semibold">
  <a href="https://inesdi-2026-prompting-workshop-slid.vercel.app/session-2/skills/peluda-context.template.md" class="inline-flex items-center gap-2 !border-none"><ph-file-text-fill class="text-xl" /> peluda-context.template.md</a>
  <a href="https://inesdi-2026-prompting-workshop-slid.vercel.app/session-2/skills/peluda-review.zip" class="inline-flex items-center gap-2 !border-none"><ph-file-zip-fill class="text-xl" /> peluda-review.zip</a>
</div>

<!--
La plantilla ya trae el frontmatter (name y description) y las reglas: solo hay que rellenar cinco huecos, y cada uno dice dónde está el dato.
Solución en demos/sesion-2/skills/peluda-context.solution.md.
Quien acabe antes: que le pida a Claude que mejore su skill con plan mode («No la cambies todavía: dime qué le falta»).
Para probarla: Kike (troll; una sola respuesta, educada, sin entrar al trapo) o Pilar (duelo con 5 estrellas: sin emojis, sin vender nada, confirmando que no habrá más envíos ni cobros). Con peluda-context, la respuesta puede usar el plan y el nombre de la mascota.
Pega en el chat de la clase la skill que has escrito y la respuesta.
-->

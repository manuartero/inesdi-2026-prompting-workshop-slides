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

# Subir, compartir, usar

<div class="grid grid-cols-3 gap-5 mt-2 items-start">
<div>

## 1 · Se sube el .md

<div class="relative">
  <img src="/captures/s2-skill-upload.png" class="w-full border border-gray-300" alt="Claude, Personalizar, Skills: subir peluda-review.md" />
  <span class="ine-hl" style="left: 24%; top: 35.4%; width: 46%; height: 3.4%" />
</div>

<p class="mt-2" style="font-size: 0.75rem; line-height: 1.4">Basta con el <b>.md</b>: nombre y descripción arriba.</p>

</div>
<div>

## 2 · Se comparte

<div class="relative">
  <img src="/captures/s2-skill-share.png" class="w-full border border-gray-300" alt="La skill subida, con los botones Share y Publish to org" />
  <span class="ine-hl" style="left: 57%; top: 14%; width: 20%; height: 4%" />
</div>

<p class="mt-2" style="font-size: 0.75rem; line-height: 1.4"><b>Share</b> o <b>Publish to org</b>: todo el equipo, la misma skill.</p>

</div>
<div>

## 3 · Se usa

<div class="relative">
  <img src="/captures/s2-skill-use.png" class="w-full border border-gray-300" alt="Un chat nuevo que empieza con /peluda-review" />
  <span class="ine-hl" style="left: 6.5%; top: 35%; width: 16.5%; height: 8.5%" />
</div>

<p class="mt-2" style="font-size: 0.75rem; line-height: 1.4">Con <b>/peluda-review</b>, o sola, cuando la descripción encaja.</p>

</div>
</div>

<p class="text-center mt-1">El prompt largo ya no se escribe. <b>Se escribe la tarea.</b></p>

<style>
.ine-hl {
  position: absolute;
  background: rgba(255, 192, 0, 0.3);
  border-bottom: 2px solid var(--ine-yellow);
}
</style>

<!--
Claude → Personalizar → Skills → subir. Acepta el .md suelto («A .md file must contain the skill name and description formatted in YAML»), o un .zip con un SKILL.md dentro.
Una vez subida: Share (a personas) o Publish to org (a toda la organización). Es el «se comparte» de la slide anterior, de verdad.
Y se llama escribiendo /peluda-review al principio del mensaje, o Claude la usa solo cuando la descripción encaja con lo que pides.
Si da tiempo, en directo: /peluda-review + la reseña de Patricia (CMS → Reseñas → «Copiar para el prompt»). Lo que hay que ver: RESPUESTA + NOTA PARA QUIEN REVISA; tú cálido (México); no repite la tarjeta ni el teléfono; pide pasar a privado; en la nota, alerta de datos personales.
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
  <a href="https://inesdi-2026-prompting-workshop-slid.vercel.app/session-2/skills/peluda-review.md" class="inline-flex items-center gap-2 !border-none"><ph-file-text-fill class="text-xl" /> peluda-review.md</a>
</div>

<!--
La plantilla ya trae el frontmatter (name y description) y las reglas: solo hay que rellenar cinco huecos, y cada uno dice dónde está el dato.
Solución en demos/sesion-2/skills/peluda-context.solution.md.
Quien acabe antes: que le pida a Claude que mejore su skill con plan mode («No la cambies todavía: dime qué le falta»).
Para probarla: Kike (troll; una sola respuesta, educada, sin entrar al trapo) o Pilar (duelo con 5 estrellas: sin emojis, sin vender nada, confirmando que no habrá más envíos ni cobros). Con peluda-context, la respuesta puede usar el plan y el nombre de la mascota.
Pega en el chat de la clase la skill que has escrito y la respuesta.
-->

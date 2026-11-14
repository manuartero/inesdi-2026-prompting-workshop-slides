---
layout: section
number: '03'
---

# Anatomía de un prompt

Adjunto · Rol · Contexto · Goal · Formato · Restricciones

---

# La versión oficial: 10 pasos

<div class="flex justify-center">
  <img src="/assets/prompt-structure.png" class="max-h-[46vh] border border-gray-300" alt="Estructura de prompt en 10 pasos, de Anthropic" />
</div>

<p class="text-center text-xs mt-2">Guía de Anthropic. CO-STAR, RTF y compañía son variantes de la misma idea: no hace falta memorizarlas.</p>

<!--
Esto es lo oficial. Completo y correcto, pero nadie escribe así en su día a día: no le sirve a nadie.
Lo que sí uso yo son seis piezas. Las vemos sobre el prompt de la demo.
-->

---
clicks: 6
---

# Las piezas, en el prompt de la demo

<PromptPieces :active="$clicks" />

<!-- Es el prompt B que lanzamos en la demo inicial. Un clic por pieza: adjunto, rol, contexto, goal, formato y restricciones; a la derecha el prompt se desplaza hasta esa pieza y la resalta. El texto sale de demos/sesion-1/01-dos-prompts.md (si cambias el prompt, actualiza components/PromptPieces.vue). -->

---

# Las seis piezas

<div class="grid grid-cols-3 gap-4 mt-2">
<div class="ine-piece"><span class="ine-piece__icon"><span class="i-ph-paperclip-fill" /></span><h3>Adjunto <code>📎</code></h3><p>Los datos de verdad: el fichero, el contrato, los tickets.</p></div>
<div class="ine-piece"><span class="ine-piece__icon"><span class="i-ph-identification-badge-fill" /></span><h3>Rol <code>&lt;rol&gt;</code></h3><p>Desde qué puesto hace el trabajo.</p></div>
<div class="ine-piece"><span class="ine-piece__icon"><span class="i-ph-buildings-fill" /></span><h3>Contexto <code>&lt;contexto&gt;</code></h3><p>Lo que sabe alguien de tu empresa y el modelo no.</p></div>
<div class="ine-piece"><span class="ine-piece__icon"><span class="i-ph-target-fill" /></span><h3>Goal <code>&lt;goal&gt;</code></h3><p>Qué tiene que conseguir, con un verbo claro.</p></div>
<div class="ine-piece"><span class="ine-piece__icon"><span class="i-ph-table-fill" /></span><h3>Formato <code>&lt;formato&gt;</code></h3><p>Cómo quieres el resultado: tabla, columnas, longitud.</p></div>
<div class="ine-piece"><span class="ine-piece__icon"><span class="i-ph-prohibit-fill" /></span><h3>Restricciones <code>&lt;restricciones&gt;</code></h3><p>Qué no debe hacer.</p></div>
</div>

---
clicks: 1
---

# Trucos que siempre funcionan

<div class="topic-list mt-2">
  <TopicRow title="Carga el contexto" icon="i-ph-paperclip-fill">pega el documento, el ticket, los datos</TopicRow>
  <TopicRow title="Define claramente el goal" icon="i-ph-target-fill">qué es «terminado». En la vida real es lo más difícil: articular qué quieres ya es un buen ejercicio</TopicRow>
  <TopicRow title="Di qué no debe hacer" icon="i-ph-prohibit-fill">«no inventes cifras», «no cambies el tono»</TopicRow>
  <TopicRow title="Opcional: enséñalo con un ejemplo" icon="i-ph-lightbulb-fill">uno o dos casos resueltos, si el formato no basta</TopicRow>
  <TopicRow v-click title="A los LLM les encantan las etiquetas" tone="warning" icon="i-ph-code-fill">
    <code>&lt;ticket&gt;…&lt;/ticket&gt;</code>, <code>&lt;contrato&gt;…&lt;/contrato&gt;</code>: el nombre de la etiqueta ya le dice qué está leyendo
  </TopicRow>
</div>

<p v-click="1" class="text-xs mt-4">Lo recomiendan las guías oficiales de <b>Anthropic</b>, <b>OpenAI</b> y <b>Google</b>. OpenAI lo midió: con documentos largos, las etiquetas funcionan bien y JSON, «particularmente mal».</p>

<!--
Siempre preguntan de dónde sale lo de las etiquetas. Las fuentes, todas oficiales:
- Anthropic, «Prompting best practices» → «Structure prompts with XML tags»: "XML tags help Claude parse complex prompts unambiguously". platform.claude.com/docs/en/build-with-claude/prompt-engineering/use-xml-tags
- OpenAI, «Prompt engineering» → «Message formatting with Markdown and XML»: "XML tags can help delineate where one piece of content begins and ends". developers.openai.com/api/docs/guides/prompt-engineering
- OpenAI, «GPT-4.1 Prompting Guide» → «Delimiters»: probaron varios delimitadores con documentos largos. "XML performed well in our long context testing." / "JSON performed particularly poorly." developers.openai.com/cookbook/examples/gpt4-1_prompting_guide
- Google, «Prompt design strategies» (Gemini 3): "XML-style tags (e.g., <context>, <task>) or Markdown headings are effective". aistudio.google.com/docs/prompting-strategies
Los nombres de las etiquetas los eliges tú: no hay una lista oficial. Lo que importa es que sean descriptivos y consistentes.
-->

---

# Cómo escribo yo los prompts: como Íñigo Montoya

<div class="grid grid-cols-[1fr_1.8fr] gap-6 mt-2">
<div>
  <img src="/assets/montoya.png" class="max-h-[20vh] mx-auto" alt="Boceto de Íñigo Montoya" />
  <p class="text-sm italic leading-snug mt-2">«Hola. Me llamo Íñigo Montoya.<br />Tú mataste a mi padre.<br />Prepárate a morir.»</p>
  <p class="text-xs">Quién soy · qué pasa · qué espero.</p>
</div>
<div>

```text
<contexto>
Soy responsable de atención al cliente de Peluda,
comida para mascotas por suscripción.
</contexto>

<problema>
Este ticket lleva 3 días sin respuesta
y la clienta está enfadada.
</problema>

<ticket>
[pega aquí el ticket]
</ticket>

Redacta una respuesta de menos de 120 palabras,
con el tono de nuestra guía de marca.
```

</div>
</div>

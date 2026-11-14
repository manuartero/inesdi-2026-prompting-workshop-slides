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
clicks: 3
---

# Cómo escribo yo los prompts: como Íñigo Montoya

<div class="grid grid-cols-[1fr_1.8fr] gap-6 mt-2 items-start">
<div>
  <img src="/assets/montoya.png" class="max-h-[16vh] mx-auto" alt="Boceto de Íñigo Montoya" />
  <div class="montoya mt-3" :class="{ 'montoya--focus': $clicks > 0 }">
    <p class="montoya__part" :class="{ 'montoya__part--on': $clicks === 1 }"><span class="montoya__num">1</span><span><i>«Hola. Me llamo Íñigo Montoya.</i><br /><small>quién soy</small></span></p>
    <p class="montoya__part" :class="{ 'montoya__part--on': $clicks === 2 }"><span class="montoya__num">2</span><span><i>Tú mataste a mi padre.</i><br /><small>qué pasa</small></span></p>
    <p class="montoya__part" :class="{ 'montoya__part--on': $clicks === 3 }"><span class="montoya__num">3</span><span><i>Prepárate a morir.»</i><br /><small>qué espero</small></span></p>
  </div>
</div>
<div class="montoya montoya__prompt" :class="{ 'montoya--focus': $clicks > 0 }">
<div class="montoya__part" :class="{ 'montoya__part--on': $clicks === 1 }"><span class="montoya__num">1</span><pre>&lt;contexto&gt;
Soy responsable de atención al cliente de Peluda,
comida para mascotas por suscripción.
&lt;/contexto&gt;</pre></div>
<div class="montoya__part" :class="{ 'montoya__part--on': $clicks === 2 }"><span class="montoya__num">2</span><pre>&lt;problema&gt;
Este ticket lleva 3 días sin respuesta
y la clienta está enfadada.
&lt;/problema&gt;
<span></span>
&lt;ticket&gt;
[pega aquí el ticket]
&lt;/ticket&gt;</pre></div>
<div class="montoya__part" :class="{ 'montoya__part--on': $clicks === 3 }"><span class="montoya__num">3</span><pre>Redacta una respuesta de menos de 120 palabras,
con el tono de nuestra guía de marca.</pre></div>
</div>
</div>

<style>
.montoya__part {
  display: flex;
  align-items: flex-start;
  gap: 0.6rem;
  margin: 0 0 0.35rem;
  padding: 0.3rem 0.5rem;
  font-size: 0.9rem;
  line-height: 1.3;
  transition: opacity 0.3s, background-color 0.3s;
}
.montoya small {
  color: var(--ine-muted);
  font-size: 0.7rem;
}
.montoya__num {
  flex: none;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 1.4rem;
  height: 1.4rem;
  border-radius: 9999px;
  background: var(--ine-yellow);
  font-size: 0.7rem;
  font-weight: 600;
  font-style: normal;
}
.montoya__prompt {
  background: white;
  border: 1.5px solid var(--ine-line);
  padding: 0.6rem;
}
.montoya__prompt pre {
  margin: 0;
  padding: 0 !important;
  background: none !important;
  font-family: 'JetBrains Mono', ui-monospace, monospace;
  font-size: 0.68rem;
  line-height: 1.55;
}
.montoya--focus .montoya__part {
  opacity: 0.3;
}
.montoya--focus .montoya__part--on {
  opacity: 1;
  background: color-mix(in srgb, var(--ine-yellow) 28%, white);
}
</style>

<!-- Clic a clic: cada frase de Íñigo es una parte del prompt. 1 quién soy → contexto; 2 qué pasa → el problema y el ticket; 3 qué espero → la orden final. -->

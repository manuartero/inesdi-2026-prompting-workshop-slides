---
layout: section
number: '05'
---

# Práctica guiada · Caso 1 · Tickets

Un ticket, tres prompts

---

# El ticket de Lucía

<div class="grid grid-cols-[1.3fr_1fr] gap-8 mt-2">
<div>

<div class="ine-tile">
  <span class="ine-tile__icon"><span class="i-ph-envelope-simple-fill" /></span>
  <h3>Me habéis cobrado dos veces</h3>
  <p class="ine-tile__example">«Hola, mirando el banco veo dos cargos de Peluda el mismo día, uno de 29 € y otro de 45 €. ¿Me podéis explicar qué ha pasado y devolverme el que sobra? Gracias.»</p>
  <p class="ine-tile__remedy"><b>Tu tarea:</b> redactar la respuesta.</p>
</div>

</div>
<div class="topic-list">
  <TopicRow title="1" icon="i-ph-browser-fill">abre el CMS de Peluda</TopicRow>
  <TopicRow title="2" icon="i-ph-tray-fill">Tickets → Hoy → «Me habéis cobrado dos veces»</TopicRow>
  <TopicRow title="3" icon="i-ph-chat-circle-text-fill">prueba los tres prompts en Claude o ChatGPT</TopicRow>
  <TopicRow title="4" icon="i-ph-paper-plane-tilt-fill">pega en el chat de la clase la respuesta que más te guste</TopicRow>
</div>
</div>

<div class="ine-todo mt-6">TODO: enlace al CMS (cuando esté desplegado en Vercel)</div>

<!-- La fecha del mensaje y el ID del ticket cambian con el día: el CMS mueve todo a hoy. Buscad el asunto, no el ID. -->

---
clicks: 1
---

# Tres versiones del mismo prompt

<div class="topic-list mt-2">
  <TopicRow title="v1 · Una línea" icon="i-ph-text-t-fill">«Responde a este ticket.» + el mensaje. ¿Qué hace con el «cobro doble»?</TopicRow>
  <TopicRow title="v2 · Con estructura" icon="i-ph-stack-fill">+ rol, goal, formato y restricciones. Mejor tono… ¿pero sabe ya si el cobro es doble?</TopicRow>
  <TopicRow title="v3 · Con los datos" icon="i-ph-paperclip-fill">el mismo prompt, con lo que da «Copiar para el prompt»: el ticket, sus suscripciones y sus pedidos</TopicRow>
  <TopicRow v-click title="No le faltaban instrucciones" tone="warning" icon="i-ph-lightbulb-fill">le faltaban datos. Lucía tiene dos suscripciones: Coco (gato, 29 €) y Bruno (perro, 45 €). No hay nada que devolver: hay que explicarlo.</TopicRow>
</div>

<!-- Es la trampa del 0009 que ya salió en la demo inicial: ni el prompt B la resolvía, porque solo veía el ticket. Prompts y resultados en demos/sesion-1/03-practica.md. -->

---

# El prompt v2 (y v3)

```text
<rol>Agente de atención al cliente de Peluda</rol>

<contexto>
Peluda vende comida para mascotas por suscripción:
cada 4 semanas enviamos un pedido a casa.
</contexto>

<ticket>
[v2: pega aquí el mensaje · v3: pega lo que da «Copiar para el prompt»]
</ticket>

<goal>Redacta la respuesta a este cliente.</goal>

<formato>Menos de 120 palabras. Cercana, sin tecnicismos. Tutea.</formato>

<restricciones>
- No prometas devoluciones ni compensaciones que no puedas comprobar.
- Si te falta información para responder, dilo.
</restricciones>
```

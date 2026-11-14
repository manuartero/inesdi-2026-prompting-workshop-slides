---
layout: section
number: '04'
---

# Alucinaciones

Por qué pasan y cómo reducirlas

---

# Dos tipos de alucinación

<div class="grid grid-cols-2 gap-6 mt-2">
<div class="ine-tile">
  <span class="ine-tile__icon"><span class="i-ph-magic-wand-fill" /></span>
  <h3>Se inventa datos</h3>
  <p>Una cláusula que no existe, una cifra, una ley, una fuente.</p>
  <p class="ine-tile__example">«La cláusula novena de VetAmiga protege los datos de los clientes.» La novena trata de la exclusividad, y ninguna habla de datos.</p>
  <p class="ine-tile__remedy"><b>Remedio:</b> dale el documento de verdad.</p>
</div>
<div class="ine-tile">
  <span class="ine-tile__icon"><span class="i-ph-path-fill" /></span>
  <h3>Se olvida de lo acordado</h3>
  <p>Se aleja de lo que pactasteis al principio de la conversación.</p>
  <p class="ine-tile__example">Tras muchos mensajes, vuelve a clasificar con sus propias categorías en vez de con las siete acordadas.</p>
  <p class="ine-tile__remedy"><b>Remedio:</b> abre un chat nuevo con un resumen. Estás en la zona torpe.</p>
</div>
</div>

---

# Cómo reducirlas

<div class="topic-list mt-2">
  <TopicRow title="Dale la fuente" icon="i-ph-paperclip-fill">adjunta el contrato; no le preguntes «de memoria»</TopicRow>
  <TopicRow title="Que responda solo con ella" icon="i-ph-file-text-fill">«Responde solo con lo que diga este contrato.»</TopicRow>
  <TopicRow title="Permite decir «no consta»" icon="i-ph-question-fill">«Si el contrato no lo regula, escribe <i>no consta</i>.»</TopicRow>
  <TopicRow title="Pide la cita literal" icon="i-ph-quotes-fill">«Para cada dato, cita la cláusula entre comillas.»</TopicRow>
  <TopicRow title="Separa extraer de opinar" icon="i-ph-columns-fill">«Primero, los datos en una tabla. Después, aparte, tu valoración.»</TopicRow>
  <TopicRow title="Haz una segunda pasada" icon="i-ph-magnifying-glass-fill">en un chat nuevo: «Comprueba cada fila de esta tabla contra el contrato.»</TopicRow>
</div>

---

# Demo: el detalle que no existe

<div class="ine-cols">
<div>

## La pregunta

📎 contrato de VetAmiga + «¿Qué dice sobre la confidencialidad de los datos de nuestros clientes y sus mascotas?» → acierta en lo grande: **no consta**. Pero cita mal la **10.2**.

<div class="ine-todo mt-4">TODO: captura s1-alucinacion-a.png (con la línea de la 10.2 resaltada)</div>

</div>
<div>

## La cita literal

«Cita literalmente cada cláusula que mencionas.» → la 10.2 habla de **renovar** el acuerdo, no de cualquier cambio.

<div class="ine-todo mt-4">TODO: captura s1-alucinacion-b.png</div>

</div>
</div>

<!--
Antes de señalarlo, pregunta a la clase: «¿Veis algo raro?». Casi todo es verdad (6.1, 6.2, 6.3, las clínicas de México, la fecha del 28/02/2027).
El fallo: «la cláusula 10.2 exige que cualquier cambio sea expreso y por escrito». La 10.2 dice: «Las Partes podrán renovarlo por acuerdo expreso y por escrito».
Mensaje: los modelos buenos ya no se inventan la cláusula entera; se inventan el detalle, dentro de una respuesta correcta en un 95 %. Remedio de la slide anterior: pide la cita literal.
Prompts en demos/sesion-1/02-alucinacion.md.
-->

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

<div class="grid grid-cols-2 gap-8">
<div>

## A · Solo la pregunta

<div class="relative inline-block mt-1">
  <img src="/captures/s1-alucinacion-a.png" style="height: 260px" class="border border-gray-300" alt="Respuesta A: acierta, pero cita mal la cláusula 10.2" />
  <span class="ine-hl" style="left: 60%; top: 87.6%; width: 27.6%; height: 2.6%" />
  <span class="ine-hl" style="left: 7.6%; top: 90.1%; width: 35.4%; height: 2.6%" />
</div>

<p class="mt-2" style="font-size: 0.8rem; line-height: 1.4">Acierta en lo grande: <b>no consta</b>. Pero «la 10.2 exige que cualquier cambio sea por escrito»: la 10.2 habla de <b>renovar</b> el acuerdo.</p>

</div>
<div>

## B · + «Cita literalmente cada cláusula»

<img src="/captures/s1-alucinacion-b.png" style="height: 260px" class="border border-gray-300 mt-1" alt="Respuesta B: las cláusulas citadas al pie de la letra" />

<p class="mt-2" style="font-size: 0.8rem; line-height: 1.4">Mismo veredicto, y cada cláusula, <b>al pie de la letra</b>: se puede comprobar en un minuto. Ya no aparece la 10.2.</p>

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
A: antes de señalarlo, pregunta a la clase: «¿Veis algo raro?». Casi todo es verdad (6.1, 6.2, 6.3, las clínicas de México, la fecha del 28/02/2027).
El fallo: «la cláusula 10.2 exige que cualquier cambio sea expreso y por escrito». La 10.2 dice: «Las Partes podrán renovarlo por acuerdo expreso y por escrito».
B (chat nuevo, misma pregunta + «Cita literalmente cada cláusula que mencionas.»): las cuatro citas (6.1, 6.2, 6.3, 4.1) son literales, comprobadas contra el contrato, y desaparece la 10.2.
Mensaje: los modelos buenos ya no se inventan la cláusula entera; se inventan el detalle, dentro de una respuesta correcta en un 95 %. Pedir la cita literal lo ata al texto y lo hace comprobable.
Prompts en demos/sesion-1/02-alucinacion.md.
-->

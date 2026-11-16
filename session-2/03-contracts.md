---
layout: section
number: '03'
---

# Caso 2 · Contratos

Documentos largos: extraer y marcar riesgos

---

# Tres contratos con trampa

<div class="grid grid-cols-3 gap-4 mt-2">
<div class="ine-card"><h3>NutriCan Ibérica</h3>Fabricante del pienso.</div>
<div class="ine-card"><h3>Rutas Levante</h3>Transporte y última milla.</div>
<div class="ine-card"><h3>Red VetAmiga</h3>Clínicas veterinarias colaboradoras.</div>
</div>

## El encargo

- **Extrae** los datos clave en una tabla: partes, duración, renovación, precio, penalizaciones.
- **Marca los riesgos** citando la cláusula. Si algo no está, **«no consta»**.

<p class="text-sm mt-6" style="color: var(--ine-muted)"><ph-download-simple-bold /> En el CMS: <b>Proveedores y contratos</b> → el proveedor → <b>Descargar contrato</b>, y se adjunta al chat.</p>

<!-- VetAmiga ya salió en la sesión 1 (la demo de alucinación). Hoy: NutriCan en la demo y Rutas Levante en la práctica. -->

---

# Demo: el contrato de NutriCan

<div class="grid grid-cols-[1fr_2fr] gap-8 mt-2">
<div>

## A · Una línea

```text
[adjunto: el contrato]

Resúmeme este contrato.
```

</div>
<div>

## B · Con estructura

```text
[adjunto: el contrato]

<rol>Responsable de compras de Peluda</rol>

<goal>
1. Tabla: partes, duración, renovación, precio,
   penalizaciones y plazos para reclamar.
2. Los riesgos para Peluda, de mayor a menor.
</goal>

<restricciones>
- Solo con lo que diga el contrato.
- Para cada dato y cada riesgo, cita la cláusula.
- Si algo no está, escribe «no consta».
- Hoy es [la fecha de hoy].
</restricciones>
```

</div>
</div>

<!--
«Hoy es…» importa: sin la fecha, el modelo no puede saber que el plazo para no renovar ya pasó.
B es «dividir en pasos» dentro de un solo prompt: primero extraer, después opinar.
Prompts en demos/sesion-2/01-contratos.md.
-->

---
clicks: 2
---

# Lo que tenía que encontrar

<div class="grid grid-cols-2 gap-6 mt-2">
<div v-click="1" class="ine-tile">
  <span class="ine-tile__icon"><span class="i-ph-arrows-clockwise-fill" /></span>
  <h3>Se ha renovado solo</h3>
  <p>La 10.1 dice que vence el 31/12/2026. La <b>14.2</b>, escondida en «Disposiciones generales», lo prorroga dos años si nadie avisa con 90 días.</p>
  <p class="ine-tile__example">El plazo acabó el 02/10/2026. Seguimos hasta 2028, y con un 4 % extra de subida.</p>
</div>
<div v-click="2" class="ine-tile">
  <span class="ine-tile__icon"><span class="i-ph-timer-fill" /></span>
  <h3>48 horas para reclamar</h3>
  <p>La <b>5.4</b>: si un lote puede dañar a los animales, Peluda tiene 48 horas para avisar por escrito. Si no, pierde todo derecho a reclamar.</p>
  <p class="ine-tile__example">¿Os acordáis del perro que vomita desde el pienso nuevo? El reloj empieza hoy.</p>
</div>
</div>

<div class="ine-todo mt-6">TODO: capturas A y B (s2-contratos-a.png, s2-contratos-b.png)</div>

<!--
Antes de los clics, pregunta: «¿Qué ha encontrado A? ¿Y B?». A suele resumir bien lo que está a la vista (objeto, precios, duración hasta 2026) y se le escapan las dos.
14.2: el vencimiento está en la 10.1, pero la prórroga tácita está al final, en la 14.2. 90 días antes del 31/12/2026 es el 02/10/2026.
5.4: enlaza con los tickets 0004, 0015, 0063 y 0145 de la sesión 1 y con la reseña de Rocío que viene ahora. Sin el aviso en 48 h, el fabricante queda exonerado de retirada, reposición e indemnizaciones (la 7.1 lo confirma: «sin perjuicio de lo previsto en la cláusula 5.4»).
-->

---

# Tu turno: Rutas Levante

<div class="grid grid-cols-[1.3fr_1fr] gap-8 mt-2">
<div>

<div class="ine-tile">
  <span class="ine-tile__icon"><span class="i-ph-truck-fill" /></span>
  <h3>¿Podemos salir del contrato?</h3>
  <p class="ine-tile__example">«Rutas Levante falla mucho en los pueblos. Dirección pregunta si podemos cambiar de transportista el mes que viene y cuánto nos cuesta.»</p>
  <p class="ine-tile__remedy"><b>Tu tarea:</b> la respuesta para dirección, citando las cláusulas.</p>
</div>

</div>
<div class="topic-list">
  <TopicRow title="1" icon="i-ph-download-simple-fill">descarga el contrato de Rutas Levante del CMS</TopicRow>
  <TopicRow title="2" icon="i-ph-chat-circle-text-fill">adáptale el prompt B de NutriCan</TopicRow>
  <TopicRow title="3" icon="i-ph-scales-fill">opcional: añade un abogado del diablo</TopicRow>
  <TopicRow title="4" icon="i-ph-paper-plane-tilt-fill">pega en el chat de la clase lo que cuesta salir</TopicRow>
</div>
</div>

<!--
Solución: la 12.2 parece permitir salir sin causa con 60 días de preaviso, pero acaba con «sin perjuicio de lo previsto en el Anexo II». El II.6 obliga a pagar el 35 % de la facturación media mensual de los últimos 12 meses por cada mes que falte hasta el vencimiento (28/02/2027). Y el II.5 exige un mínimo de 7.000 envíos al mes, en cómputo trimestral.
Si alguien solo cita la 12.2, ha caído en la trampa: buen momento para la segunda pasada («Comprueba cada fila contra el contrato»).
-->

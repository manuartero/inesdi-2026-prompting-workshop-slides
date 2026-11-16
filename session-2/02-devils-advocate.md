---
layout: section
kicker: "Devil's advocate"
number: '02'
---

# Devil's advocate

El abogado del diablo: que te lleve la contraria

---

# Por defecto, te da la razón

<div class="grid grid-cols-2 gap-6 mt-2">
<div class="ine-tile ine-tile--muted">
  <span class="ine-tile__icon"><span class="i-ph-thumbs-up-fill" /></span>
  <h3>Te dice que sí</h3>
  <p>Le cuentas tu idea y te ayuda a llevarla a cabo. Si la pregunta ya trae la respuesta, te la confirma.</p>
  <p class="ine-tile__example">«¿Podemos salir del contrato con 60 días de preaviso?» → «Sí, según la 12.2…»</p>
</div>
<div class="ine-tile ine-tile--accent">
  <span class="ine-tile__icon"><span class="i-ph-scales-fill" /></span>
  <h3>Te lleva la contraria</h3>
  <p>Si le das un segundo papel: el que busca todo lo que puede salir mal.</p>
  <p class="ine-tile__example">«Ahora haz de abogado del diablo: ¿qué nos puede costar salir?»</p>
</div>
</div>

<p class="mt-6"><b>Cuándo:</b> antes de una decisión, de enviar un plan o de dar por bueno un texto que ya te gusta.</p>

<!--
En inglés: «devil's advocate». Cuando se hace a fondo, buscando fallos a propósito, se llama «red teaming».
Por qué pasa: los modelos se entrenan para ser útiles y agradables, y tienden a darte la razón (en inglés, «sycophancy»). Si no le das permiso para llevarte la contraria, rara vez lo hace.
-->

---
clicks: 1
---

# Demo: ¿salimos de Rutas Levante?

<div class="grid grid-cols-[1fr_1.6fr] gap-8 mt-2">
<div>

## A · La pregunta

```text
[adjunto: el contrato]

Rutas Levante falla mucho en
los pueblos. ¿Podemos cambiar
de transportista el mes que
viene?
```

</div>
<div>

## B · + Devil's advocate

```text
[adjunto: el contrato]

Rutas Levante falla mucho en los pueblos.
Queremos cambiar de transportista el mes
que viene.

Responde dos veces, citando las cláusulas:
1. Como analista de operaciones: cómo
   salir del contrato.
2. Como abogado del diablo: todo lo que
   nos puede costar o salir mal.
```

</div>
</div>

<p v-click class="text-sm mt-3"><b>Lo que encuentra el devil's advocate:</b> la 12.2 deja salir con 60 días… «sin perjuicio del Anexo II». El <b>II.6</b>: pagar el 35&nbsp;% de la facturación media por cada mes que falte hasta el 28/02/2027. <span class="ine-todo">TODO: capturas A y B</span></p>

<!--
A suele quedarse en la 12.2: «sí, con 60 días de preaviso por escrito». Es verdad, pero no es toda la verdad.
La 12.2 termina con «sin perjuicio de lo previsto en el Anexo II». El II.6 obliga a pagar el 35 % de la facturación media mensual de los últimos 12 meses por cada mes que falte hasta el vencimiento (28/02/2027). Y el II.5 fija un mínimo de 7.000 envíos al mes, en cómputo trimestral.
Prompts en demos/sesion-2/01-abogado-del-diablo.md.
-->

---

# Tu turno: NutriCan

<div class="grid grid-cols-[1.3fr_1fr] gap-8 mt-2">
<div>

<div class="ine-tile">
  <span class="ine-tile__icon"><span class="i-ph-factory-fill" /></span>
  <h3>«Dejamos que venza y cambiamos de fabricante»</h3>
  <p class="ine-tile__example">«El contrato con NutriCan vence a final del mes que viene. No lo renovamos y luego empezamos con otro fabricante. ¿Algún problema?»</p>
  <p class="ine-tile__remedy"><b>Tu tarea:</b> que el devil's advocate lo revise, citando las cláusulas.</p>
</div>

</div>
<div class="topic-list">
  <TopicRow title="1" icon="i-ph-download-simple-fill">CMS → Proveedores y contratos → NutriCan → Descargar contrato</TopicRow>
  <TopicRow title="2" icon="i-ph-chat-circle-text-fill">adjúntalo y adapta el prompt B</TopicRow>
  <TopicRow title="3" icon="i-ph-calendar-fill">dile qué día es hoy</TopicRow>
  <TopicRow title="4" icon="i-ph-paper-plane-tilt-fill">pega en el chat de la clase el riesgo más grave</TopicRow>
</div>
</div>

<!--
Solución:
- 14.2: la 10.1 dice que vence a final del mes que viene (el 01/12, día de la sesión, pone 31/01/2027), pero la 14.2 (al final, en «Disposiciones generales») lo prorroga dos años si nadie avisa con 90 días. Ese plazo acabó hace un mes: sigue dos años más y con un 4 % extra de subida. «No lo renovamos» ya no es posible.
- 5.4: 48 horas para avisar por escrito de un lote que pueda dañar a los animales. Enlaza con el perro que vomita de los tickets (0004, 0015, 0063, 0145): antes de cambiar de fabricante, hay que reclamar ese lote.
Sin la fecha de hoy, el modelo no puede saber que el plazo de la 14.2 ya pasó: por eso el paso 3.
-->

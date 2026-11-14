---
layout: section
number: '03'
---

# Anatomía de un prompt

Rol · Contexto · Tarea · Formato · Restricciones · Ejemplos

---

# Las seis piezas

<div class="grid grid-cols-3 gap-4 mt-2">
<div class="ine-card ine-card--accent"><h3>Rol</h3>Quién es al hacer el trabajo.</div>
<div class="ine-card ine-card--accent"><h3>Contexto</h3>Lo que sabe alguien de tu empresa y el modelo no.</div>
<div class="ine-card ine-card--accent"><h3>Tarea</h3>Qué tiene que hacer, con un verbo claro.</div>
<div class="ine-card"><h3>Formato</h3>Tabla, lista, columnas, longitud.</div>
<div class="ine-card"><h3>Restricciones</h3>Qué no debe hacer.</div>
<div class="ine-card"><h3>Ejemplos</h3>Uno o dos casos resueltos.</div>
</div>

<!-- La siguiente slide recorre las seis piezas sobre el prompt B de la demo inicial. -->

---

# Las piezas, en el prompt de la demo

```text {1|3|5-8|10|12-19|21-25}{maxHeight:'60vh'}
📎 peluda-tickets-hoy.csv

<rol>Responsable del equipo de atención al cliente de Peluda</rol>

<contexto>
Peluda vende comida para mascotas por suscripción: cada 4 semanas enviamos un pedido a casa. Hay tres planes: Básico, Completo y Cuidado.
Hace unas semanas cambiamos la receta del pienso de perro adulto en España.
</contexto>

<goal>Clasifica los tickets por categoría y urgencia.</goal>

<formato>
1. Tabla con los 15 tickets más urgentes: ID | Categoría | Urgencia | Resumen | Por qué urgente.
2. Tabla con cuántos tickets hay de cada categoría y de cada urgencia.
3. Si varios tickets hablan del mismo problema, cuáles son y qué tienen en común.
Categorías: Envío, Facturación, Cambio de plan, Baja, Salud de la mascota, Cuenta, Otro.
Urgencia Alta: salud de una mascota, mascota sin comida, cobro indebido o amenaza…
</formato>

<restricciones>
- Lee todos los tickets del fichero.
- Si un ticket trata dos asuntos, clasifícalo por el más grave.
- No inventes nada. Si no puedes decidir, escribe «Revisar».
</restricciones>
```

<!-- Es el prompt que lanzamos en la demo inicial. Un clic por pieza: material adjunto, rol, contexto, tarea (goal), formato y restricciones. No lleva ejemplo: el formato ya deja claro qué tabla queremos, así que aquí no hace falta (con una salida menos obvia, sí). El prompt completo está en demos/sesion-1/01-dos-prompts.md. -->

---

# La versión oficial: 10 pasos

<div class="flex justify-center">
  <img src="/assets/prompt-structure.png" class="max-h-[46vh] border border-gray-300" alt="Estructura de prompt en 10 pasos, de Anthropic" />
</div>

<p class="text-center text-xs mt-2">Guía de Anthropic. CO-STAR, RTF y compañía son variantes de la misma idea: no hace falta memorizarlas.</p>

---
clicks: 1
---

# Trucos que siempre funcionan

<div class="flex flex-col gap-2 mt-2">
  <TopicRow title="Carga el contexto">pega el documento, el ticket, los datos</TopicRow>
  <TopicRow title="Enséñalo, no lo expliques">uno o dos ejemplos del resultado que quieres</TopicRow>
  <TopicRow title="Di qué no debe hacer">«no inventes cifras», «no cambies el tono»</TopicRow>
  <TopicRow title="Define cuándo está terminado">tabla con estas columnas, máximo 120 palabras</TopicRow>
  <TopicRow title="Itera, no empieces de cero">corrige en la misma conversación</TopicRow>
  <div v-click>
    <TopicRow title="A los LLM les encantan las etiquetas" tone="warning">
      <code>&lt;ticket&gt;…&lt;/ticket&gt;</code>, <code>&lt;contrato&gt;…&lt;/contrato&gt;</code>: el nombre de la etiqueta ya le dice qué está leyendo
    </TopicRow>
  </div>
</div>

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

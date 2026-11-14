---
theme: default
title: Prompt engineering estratégico · Sesión 1
info: Taller 1 del Máster de FP en Inteligencia Artificial Aplicada a la Empresa (INESDI, edición 2609).
colorSchema: light
aspectRatio: 16/9
fonts:
  sans: Albert Sans
  mono: JetBrains Mono
  weights: '300,400,500,600,700'
transition: fade
layout: cover
session: Sesión 1 · Prompts estructurados · martes 24/11/2026
teacher: Manuel Artero
---

# Prompt engineering estratégico

Máster de FP en Inteligencia Artificial Aplicada a la Empresa

---

# Hoy, en 90 minutos

| Min   | Bloque                                |
| ----- | ------------------------------------- |
| 0–10  | El mismo encargo, dos prompts         |
| 10–25 | Cómo «piensa» un LLM                  |
| 25–50 | Anatomía de un prompt                 |
| 50–70 | Alucinaciones                         |
| 70–85 | Práctica guiada · Caso 1 · Tickets    |
| 85–90 | Cierre: chuleta y actividad           |

---
layout: section
number: '01'
minutes: 0–10 min
---

# El mismo encargo, dos prompts

Demo en directo antes de explicar nada

---
layout: two-cols
minutes: 0–10
---

# ¿Ves la diferencia?

::left::

## Prompt de una línea

```text
📎 peluda-tickets-hoy.csv

Clasifica estos tickets.
```

<img src="/captures/s1-dos-prompts-a.png" class="mt-3 max-h-[36vh] border border-gray-300" alt="Resultado del prompt de una línea: un esquema de prioridades y categorías inventado por el modelo" />

::right::

## Prompt estructurado

```text
<rol> Responsable de atención al cliente </rol>
<contexto> Peluda, planes, 26 h de respuesta… </contexto>
<tarea> Clasifica, prioriza y resume </tarea>
<formato> Tabla: ID | Categoría | Urgencia… </formato>
<restricciones> No inventes. Si dudas: «Revisar» </restricciones>
<ejemplo> Una fila resuelta </ejemplo>
<material> 📎 la bandeja de hoy, en CSV </material>
```

<div class="ine-todo mt-4">TODO: captura s1-dos-prompts-b.png (plan B si falla la demo)</div>

<!--
Prompt A (probado el 14/11 con Opus 5.5, 151 tickets): lo hace bien, pero con SU esquema. Avisa: «No tenías un esquema propio, así que he usado este». 4 prioridades (Urgente/Alta/Normal/Baja) y ~25 categorías inventadas (Retención, Nutrición, Datos RGPD…): mañana serán otras, no se pueden contar ni comparar. Y cae en la trampa del 0009: lo junta con el 0033 como «fallo en una tanda de cobros», cuando Lucía tiene dos suscripciones.
Los dos con el mismo CSV: la bandeja de hoy exportada del CMS (Tickets → Hoy → Exportar CSV, 151 tickets). Que vean el formato inconsistente frente a la tabla. Prompts en demos/sesion-1/01-dos-prompts.md.
No explicar nada todavía.
-->

---
layout: statement
---

# Un prompt es un encargo a un **becario brillante** que no sabe nada de tu empresa.

Todo lo que no le cuentes, se lo inventa.

---

# Peluda: la empresa de este taller

<div class="grid grid-cols-3 gap-4 mt-2">
<div class="ine-card ine-card--accent">

### Qué hace

Comida para perros y gatos **por suscripción**. Cada 4 semanas, en casa.

</div>
<div class="ine-card">

### Dónde

España, México, Colombia, Perú y Argentina. 17.564 suscriptores.

</div>
<div class="ine-card">

### Con quién

**30 personas.** Un equipo pequeño que no da abasto.

</div>
</div>

## Sus tres problemas son nuestros tres casos

- **Tickets:** ~150 al día y 451 sin clasificar ahora mismo. Primera respuesta en 26 h (objetivo: 4 h).
- **Contratos:** nadie los relee y se renuevan solos.
- **Reseñas:** ~320 al mes, solo se contesta el 30 %. 224 esperan respuesta.

<!-- Empresa ficticia. Siguiente slide: su sistema, y un tour corto por el CMS. -->

---
minutes: 0–10
---

# Su sistema: Peluda Admin

<div class="grid grid-cols-3 gap-x-4 gap-y-3 mt-1">
<figure>
  <img src="/captures/cms-inicio.png" class="border border-gray-300" alt="Inicio del CMS: 451 tickets sin clasificar y 224 reseñas sin responder" />
  <figcaption class="text-xs mt-1">Inicio: lo pendiente hoy y las cifras</figcaption>
</figure>
<figure>
  <img src="/captures/cms-tickets.png" class="border border-gray-300" alt="Bandeja de tickets, filtrable por día y país" />
  <figcaption class="text-xs mt-1">Tickets: la bandeja, por día y país</figcaption>
</figure>
<figure>
  <img src="/captures/cms-ticket.png" class="border border-gray-300" alt="Detalle de un ticket con el cliente, sus mascotas y sus pedidos" />
  <figcaption class="text-xs mt-1">Un ticket, con su cliente y sus pedidos</figcaption>
</figure>
<figure>
  <img src="/captures/cms-clientes.png" class="border border-gray-300" alt="Lista de clientes con buscador" />
  <figcaption class="text-xs mt-1">Clientes: 625, con mascotas y suscripción</figcaption>
</figure>
<figure>
  <img src="/captures/cms-contratos.png" class="border border-gray-300" alt="Proveedores y contratos con su vencimiento" />
  <figcaption class="text-xs mt-1">Proveedores y contratos</figcaption>
</figure>
<figure>
  <img src="/captures/cms-resenas.png" class="border border-gray-300" alt="Reseñas sin responder" />
  <figcaption class="text-xs mt-1">Reseñas: web, app y Google</figcaption>
</figure>
</div>

<!--
Tour de 2 minutos en el CMS en directo (no en la slide):
1. Inicio: 451 tickets sin clasificar y 224 reseñas sin responder. «Este es el lunes de este equipo».
2. Tickets → filtro Hoy: 151 tickets. Botón «Exportar CSV»: así sacaremos los datos para la IA.
3. Abrir un ticket (por ejemplo, el 0009 «Me habéis cobrado dos veces»): cliente, mascotas, pedidos. «Copiar para el prompt».
4. Proveedores: NutriCan «vence pronto» (spoiler del caso 2).
5. Reseñas: 224 sin responder (caso 3, sesión 2).
Todo es inventado; lo pueden abrir después para practicar.
-->

---
layout: section
number: '02'
minutes: 10–25 min
---

# Cómo «piensa» un LLM

Solo lo que explica su comportamiento

---
minutes: 10–25
---

# El efecto Magneto

<div class="ine-cols mt-2">
<div class="ine-card">

<img src="/assets/magneto-villain.jpg" class="w-full h-32 object-cover object-top mb-2" alt="Magneto villano" />

### El villano

Levantaba submarinos y amenazaba con invertir los polos de la Tierra.

*Daba miedo porque nadie sabía dónde estaba su **techo**.*

</div>
<div class="ine-card ine-card--accent">

<img src="/assets/magneto-headmaster.jpg" class="w-full h-32 object-cover object-top mb-2" alt="Magneto director" />

### El director del colegio

El mismo poder, pero con los límites conocidos y los fallos entendidos.

*Mismo poder, techo conocido: un compañero útil.*

</div>
</div>

> Con los LLM estamos a mitad de esa conversión. Las próximas slides marcan el techo.

<!--
Magneto en los cómics de los 70–80 frente al Magneto que dirige la escuela (X-Men, 1993).
Imágenes de Marvel: uso ilustrativo en clase.
-->

---
minutes: 10–25
---

# Un JPEG borroso de internet

<div class="grid grid-cols-2 gap-8 mt-2 items-center">
<PretrainingCompression />
<div class="flex flex-col gap-2">
  <TopicRow title="Comprime con pérdida">los detalles finos se emborronan</TopicRow>
  <TopicRow title="Predice texto plausible">no consulta una base de datos: escribe lo que <i>suena</i> bien</TopicRow>
  <TopicRow title="Solo ve nítido lo que le das">tu empresa, tus clientes y tus contratos no están en el JPEG</TopicRow>
  <TopicRow title="Consecuencia" tone="warning">pega el documento de verdad; no te fíes de lo que «recuerda»</TopicRow>
</div>
</div>

<!--
Las alucinaciones son esta compresión hablando: quiere ayudar tanto que rellena
los huecos borrosos con algo que suena bien.
-->

---
minutes: 10–25
clicks: 2
---

# Cada palabra se relaciona con todas las demás

<div class="mt-4">
  <AttentionArcs :showLastWord="$clicks >= 1" :showArcs="$clicks >= 2" />
</div>

<p v-if="$clicks === 0" class="text-center">Siete palabras en la conversación.</p>
<p v-else-if="$clicks === 1" class="text-center">Llega una más. El modelo tiene que relacionarla con <b>todas</b> las anteriores.</p>
<p v-else class="text-center">8 palabras → 28 relaciones. Una palabra más ha añadido <b>7</b>. Cada palabra nueva cuesta más que la anterior.</p>

<!--
Como una liga de fútbol: cada equipo nuevo juega contra todos los demás.
Por eso una conversación el doble de larga es mucho más del doble de trabajo.
-->

---
minutes: 10–25
---

# Las conversaciones largas se degradan

<div class="flex flex-col gap-2 mt-2">
  <TopicRow title="Su atención es limitada">cuanto más larga la conversación, más se reparte</TopicRow>
  <TopicRow title="Lo reciente se ve nítido">lo del principio se vuelve borroso</TopicRow>
</div>

<div class="mt-10">
  <ContextWindowZones />
</div>

<p class="text-center mt-4">Que el chat admita más texto no amplía la zona lúcida: solo añade <b>zona torpe</b>.</p>

---
minutes: 10–25
---

# Cada chat empieza de cero

<div class="flex flex-col gap-2 mt-2">
  <TopicRow title="Sin memoria">cada conversación nueva es un becario nuevo, el primer día</TopicRow>
  <TopicRow title="Congelado en el tiempo">no sabe nada de lo que pasó después de su entrenamiento</TopicRow>
  <TopicRow title="La conversación es su memoria de trabajo">lo que hay en el chat es todo lo que tiene</TopicRow>
</div>

---
minutes: 10–25
---

# Cuatro límites, un remedio

<div class="flex flex-col gap-2 mt-2">
  <TopicRow title="Memoria borrosa">es un JPEG borroso de internet</TopicRow>
  <TopicRow title="Atención limitada">las conversaciones largas se degradan</TopicRow>
  <TopicRow title="Sin memoria">cada chat empieza de cero</TopicRow>
  <TopicRow title="Fecha de corte">congelado en el tiempo</TopicRow>
</div>

<blockquote class="mt-6 text-lg">

Los cuatro empujan hacia lo mismo: **pon en la conversación lo que importa, y solo lo que importa.**

</blockquote>

El resto del taller son tácticas para eso.

---
layout: section
number: '03'
minutes: 25–50 min
---

# Anatomía de un prompt

Rol · Contexto · Tarea · Formato · Restricciones · Ejemplos

---
minutes: 25–50
---

# Las seis piezas

<div class="grid grid-cols-3 gap-4 mt-2">
<div class="ine-card ine-card--accent"><h3>Rol</h3>Quién es al hacer el trabajo.</div>
<div class="ine-card ine-card--accent"><h3>Contexto</h3>Lo que sabría un empleado y el becario no.</div>
<div class="ine-card ine-card--accent"><h3>Tarea</h3>Qué tiene que hacer, con un verbo claro.</div>
<div class="ine-card"><h3>Formato</h3>Tabla, lista, columnas, longitud.</div>
<div class="ine-card"><h3>Restricciones</h3>Qué no debe hacer.</div>
<div class="ine-card"><h3>Ejemplos</h3>Uno o dos casos resueltos.</div>
</div>

<!-- La siguiente slide recorre las seis piezas sobre el prompt B de la demo inicial. -->

---
minutes: 25–50
---

# Las seis piezas, en el prompt de la demo

```text {1|2-4|5|6-8|9-10|11|12}{maxHeight:'58vh'}
<rol>Eres responsable de atención al cliente de Peluda.</rol>
<contexto>Comida para perros y gatos por suscripción en 5 países.
Unos 150 tickets al día; primera respuesta en 26 h (objetivo: 4 h).
Hace unas semanas cambiamos la receta del pienso de perro.</contexto>
<tarea>Clasifica cada ticket por categoría y urgencia y resúmelo.</tarea>
<formato>Las 15 más urgentes: ID | Categoría | Urgencia | Resumen.
Categorías, solo estas: Envío · Facturación · Cambio de plan · …
Si varios tickets hablan del mismo problema, dilo al final.</formato>
<restricciones>No inventes nada que no esté en el ticket.
Si no puedes decidir, escribe «Revisar».</restricciones>
<ejemplo>| TCK-EJEMPLO | Salud de la mascota | Alta | … |</ejemplo>
<material>📎 La bandeja de hoy, exportada del sistema (CSV).</material>
```

<!-- Un clic por pieza: rol, contexto, tarea, formato, restricciones, ejemplo y, al final, el material. El material va adjunto, no pegado: así se trabaja de verdad. El prompt completo está en demos/sesion-1/01-dos-prompts.md. -->

---
minutes: 25–50
---

# La versión oficial: 10 pasos

<div class="flex justify-center">
  <img src="/assets/prompt-structure.png" class="max-h-[46vh] border border-gray-300" alt="Estructura de prompt en 10 pasos, de Anthropic" />
</div>

<p class="text-center text-xs mt-2">Guía de Anthropic. CO-STAR, RTF y compañía son variantes de la misma idea: no hace falta memorizarlas.</p>

---
minutes: 25–50
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
minutes: 25–50
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

---
layout: section
number: '04'
minutes: 50–70 min
---

# Alucinaciones

Por qué pasan y cómo reducirlas

---
minutes: 50–70
---

# Dos tipos de alucinación

<div class="ine-cols mt-2">
<div class="ine-card ine-card--accent">

### Se inventa datos

Una cláusula que no existe, una cifra, una ley, una fuente.

**Remedio:** dale el documento de verdad.

</div>
<div class="ine-card">

### Se olvida de lo acordado

Se aleja de lo que pactasteis al principio de la conversación.

**Remedio:** abre un chat nuevo con un resumen. Estás en la zona torpe.

</div>
</div>

---
minutes: 50–70
---

# Cómo reducirlas

<div class="ine-cols">
<div>

- Dale **la fuente**.
- «Responde **solo** con este documento».
- Permite decir **«no consta»**.

</div>
<div>

- Pide la **cita literal**.
- **Separa** extraer de opinar.
- Haz una **segunda pasada** de verificación.

</div>
</div>

---
minutes: 50–70
---

# Demo: la cláusula que no existe

<div class="ine-cols">
<div>

## Sin instrucciones

📎 contrato de VetAmiga + «¿Qué dice sobre la confidencialidad de los datos?» → el modelo **se la inventa**.

<div class="ine-todo mt-4">TODO: captura s1-alucinacion-a.png</div>

</div>
<div>

## Con instrucciones

«Responde solo con el contrato y cita la cláusula. Si no lo regula, di *no consta*.» → **no consta**.

<div class="ine-todo mt-4">TODO: captura s1-alucinacion-b.png</div>

</div>
</div>

<!-- Contrato de Red VetAmiga: no tiene cláusula de confidencialidad ni de protección de datos. Prompts en demos/sesion-1/02-alucinacion.md. -->

---
layout: section
number: '05'
minutes: 70–85 min
---

# Práctica guiada · Caso 1 · Tickets

Mejoramos un prompt entre todos en 3 iteraciones

---
minutes: 70–85
---

# De categoría, urgencia y resumen

| Iteración | Qué cambiamos                                    | Qué mejora             |
| --------- | ------------------------------------------------ | ---------------------- |
| v1        | Prompt de una línea                              | —                      |
| v2        | + contexto de Peluda y categorías cerradas       | Formato consistente    |
| v3        | + criterios de urgencia y un ejemplo             | Aflora el urgente      |

> Pista: hay un perro que vomita desde que cambió al pienso nuevo. ¿Lo encuentra tu prompt?

<div class="ine-todo mt-4">TODO: enlace al CMS. Tickets → Hoy → Exportar CSV, adjúntalo y pega tu prompt.</div>

---
layout: section
number: '06'
minutes: 85–90 min
---

# Cierre

---
layout: statement
---

Antes de cada tarea, una pregunta:

# ¿Puede la IA **hacer esto por mí**, o hacerlo más rápido?

---
minutes: 85–90
---

# Para llevarte

<div class="ine-cols">
<div class="ine-card ine-card--accent">

### La chuleta

Plantilla de prompt + checklist antialucinaciones.

<div class="ine-todo mt-2">TODO: enlace al PDF</div>

</div>
<div class="ine-card">

### Hasta el 01/12 (voluntario)

Trae una **tarea real** de tu trabajo y resuélvela con la plantilla. Entrega:

- el prompt inicial,
- el final,
- qué cambió.

</div>
</div>

---
layout: end
---

Nos vemos el martes 01/12/2026

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

# Sobre mí

<div class="text-2xl font-semibold leading-tight mt-2">Manu Artero Anguita</div>
<div class="text-base mt-1">Principal Engineer en la Plataforma Global de Vídeo de Telefónica</div>

<div class="grid grid-cols-[auto_6.5rem_1fr] gap-x-4 gap-y-3 items-center mt-6 text-base">
  <span class="inline-flex items-center justify-center w-10 h-10 rounded-full" style="background: var(--ine-yellow)"><ph-robot-fill class="text-xl" /></span><b>Ahora</b><span>agentes, skills y servidores MCP: la plataforma de tooling de IA del equipo</span>
  <span class="inline-flex items-center justify-center w-10 h-10 rounded-full" style="background: var(--ine-yellow)"><ph-stack-fill class="text-xl" /></span><b>Antes</b><span>full stack; líder de backend en Doctor24 y de equipo en TV Apps</span>
  <span class="inline-flex items-center justify-center w-10 h-10 rounded-full" style="background: var(--ine-yellow)"><ph-chalkboard-teacher-fill class="text-xl" /></span><b>En INESDI</b><span>profesor de Frontend Frameworks (React) → Prompt engineering estratégico</span>
  <span class="inline-flex items-center justify-center w-10 h-10 rounded-full" style="background: var(--ine-yellow)"><ph-graduation-cap-fill class="text-xl" /></span><b>Formación</b><span>Informática, Universidad Complutense de Madrid</span>
</div>

<div class="flex gap-8 mt-8 text-sm items-center whitespace-nowrap">
  <a href="https://www.linkedin.com/in/manu-artero/" class="flex items-center gap-2"><ph-linkedin-logo-fill class="text-3xl" style="color: #0a66c2" /> manu-artero</a>
  <a href="https://github.com/manuartero" class="flex items-center gap-2"><ph-github-logo-fill class="text-3xl" style="color: #181717" /> manuartero</a>
  <a href="https://dev.to/manuartero" class="flex items-center gap-2"><ph-dev-to-logo-fill class="text-3xl" style="color: #0a0a0a" /> manuartero</a>
</div>

<!--
No es por ego: es para que sepan quién les habla y por qué. Un minuto, como mucho.
- Trabajo con agentes de IA a diario: es mi trabajo ahora mismo, no algo que he leído.
- Ya daba clase en INESDI (Frontend Frameworks): esto es lo mismo, pero sin código.
- Si sale el tema: escribía en dev.to; el último post que dio que hablar, «About Wizards & Warlocks, Programmers & Vibe Coders» (el mago estudia su magia; al brujo se la presta un patrón, que puede cambiar las condiciones).
-->

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

<img src="/captures/s1-dos-prompts-a.png" class="mt-3 w-full border border-gray-300" style="height: 200px; object-fit: cover; object-position: top" alt="Resultado del prompt de una línea: un esquema de prioridades y categorías inventado por el modelo" />

::right::

## Prompt estructurado

```text
📎 peluda-tickets-hoy.csv

<rol>Responsable de atención al cliente</rol>
<contexto>Suscripción cada 4 semanas, 3 planes.
Hace semanas cambiamos la receta de perro.</contexto>
<goal>Clasifica por categoría y urgencia.</goal>
<formato>1. Los 15 urgentes 2. Recuento 3. Qué se repite
Categorías: Envío, Facturación… Urgencia: Alta…</formato>
<restricciones>Lee todos. No inventes. «Revisar».</restricciones>
```

<img src="/captures/s1-dos-prompts-b-urgentes.png" class="mt-3 w-full border border-gray-300" style="height: 140px; object-fit: cover; object-position: 50% 9%" alt="Resultado del prompt estructurado: tabla de los 15 tickets más urgentes" />

<!--
Prompt A (probado el 14/11 con Opus 5.5, 151 tickets): lo hace bien, pero con SU esquema. Avisa: «No tenías un esquema propio, así que he usado este». 4 prioridades (Urgente/Alta/Normal/Baja) y ~25 categorías inventadas (Retención, Nutrición, Datos RGPD…): mañana serán otras, no se pueden contar ni comparar. Y cae en la trampa del 0009: lo junta con el 0033 como «fallo en una tanda de cobros», cuando Lucía tiene dos suscripciones.
Los dos con el mismo CSV: la bandeja de hoy exportada del CMS (Tickets → Hoy → Exportar CSV, 151 tickets). Que vean el formato inconsistente frente a la tabla. Prompts en demos/sesion-1/01-dos-prompts.md.
No explicar nada todavía.
-->

---
minutes: 0–10
---

# El prompt de una línea, revisado contra el sistema

<div class="flex flex-col gap-1 mt-1">
  <TopicRow title="Se inventa el esquema">«No tenías un esquema propio, así que he usado este»: 25 categorías. En la misma respuesta mezcla «Salud» y «Salud/calidad», y separa «Cobros», «Pago» y «Facturas».</TopicRow>
  <TopicRow title="Mete a una gata de Colombia en el problema de la receta">0123: Luna es una gata en Colombia, con otro fabricante. La receta que cambió es la del pienso de perro adulto en España.</TopicRow>
  <TopicRow title="«Puede ser un fallo en una tanda de cobros»">0009 y 0062 tienen dos suscripciones: dos pedidos el mismo día, con importes distintos. 0033 es un cobro después de la baja. 0020 no tiene ningún cobro duplicado en el sistema.</TopicRow>
  <TopicRow title="Mismo caso, distinta urgencia">Dos bajas por fallecimiento: 0024 es «Urgente» y 0058, «Alta».</TopicRow>
  <TopicRow title="Cuenta mal su propia tabla" tone="warning">Dice «98 normales y 11 bajas». En su tabla hay 97 y 12.</TopicRow>
</div>

<p class="text-sm mt-4">Suena seguro y casi todo es verdad. Por eso cuesta ver lo que no lo es.</p>

<!--
Comprobado contra el CMS (14/11). Lo que SÍ hizo bien, para ser justos: ve el patrón de la receta (0004/0145, 0015, 0063), propone fusionar 0004 y 0145 (es la misma clienta) y sus «Ver 00xx» enlazan tickets del mismo cliente (usa la columna ID cliente).
- 0009 Lucía: 23/10, ORD-…296361 29 € (Básico, Coco) y ORD-…296182 45 € (Completo, Bruno).
- 0062 (Colombia): 13/10 y 10/11, dos pedidos cada día, 129.000 y 199.000 COP, dos suscripciones.
- 0020 (México): una sola suscripción, ningún pedido con dos cobros.
- 0123: PRD-KIBBLE-ADULT-CAT-LATAM, fabricante Alimentos del Bajío. La receta nueva es PRD-KIBBLE-ADULT-DOG, solo España, de NutriCan.
Mensaje: no son mentiras grandes, son conclusiones sin datos. El modelo no sabía nada de Peluda y rellenó los huecos.
-->

---
minutes: 0–10
---

# Con estructura, el resultado se puede usar

<div class="grid grid-cols-3 gap-5 mt-1">
<figure>
  <img src="/captures/s1-dos-prompts-b-urgentes.png" class="w-full border border-gray-300" style="height: 270px; object-fit: cover; object-position: top" alt="Los 15 tickets más urgentes" />
  <figcaption class="text-sm mt-2"><b>1 · Los 15 urgentes.</b> Arriba, el perro que vomita: une el 0004 y el 0145.</figcaption>
</figure>
<figure>
  <img src="/captures/s1-dos-prompts-b-recuento.png" class="w-full border border-gray-300" style="height: 270px; object-fit: cover; object-position: bottom" alt="Recuento por categoría y urgencia" />
  <figcaption class="text-sm mt-2"><b>2 · El recuento.</b> Nuestras 7 categorías, suman 151. Mañana se puede comparar.</figcaption>
</figure>
<figure>
  <img src="/captures/s1-dos-prompts-b-patrones.png" class="w-full border border-gray-300" style="height: 270px; object-fit: contain; background: #262624" alt="Criterios decididos por el modelo y problemas repetidos" />
  <figcaption class="text-sm mt-2"><b>3 · Lo que se repite.</b> La receta nueva. Y te dice qué criterios tuvo que decidir él.</figcaption>
</figure>
</div>

<!--
Prompt B probado el 14/11 con Opus 5.5 sobre los 151 tickets de hoy.
- Los 15 urgentes: 0145 (+0004, la misma clienta), 0063 (la clínica VetAmiga), 0123, 0015… El hilo de la receta sale arriba.
- Recuento con NUESTRAS 7 categorías y 3 urgencias: 20 alta, 47 media, 84 baja. Con el prompt A eran ~25 categorías inventadas.
- «Criterios que he tenido que decidir yo»: qué cuenta como amenaza, dudas de alimentación sin síntomas… Son los huecos de nuestro prompt: la siguiente iteración los cierra.
- Sigue marcando el 0009 (Lucía) como «probable cobro indebido»: con el ticket solo no puede saber que tiene dos suscripciones. Le faltan datos, no instrucciones → «Copiar para el prompt» del CMS añade los pedidos.
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

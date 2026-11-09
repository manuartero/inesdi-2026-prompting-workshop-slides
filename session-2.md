---
theme: default
title: Prompt engineering estratégico · Sesión 2
info: Taller 1 del Máster de FP en Inteligencia Artificial Aplicada a la Empresa (INESDI, edición 2609).
colorSchema: light
aspectRatio: 16/9
fonts:
  sans: Albert Sans
  mono: JetBrains Mono
  weights: '300,400,500,600,700'
transition: fade
layout: cover
session: Sesión 2 · Flujos de trabajo · martes 01/12/2026
teacher: Manuel Artero
---

# Prompt engineering estratégico

Máster de FP en Inteligencia Artificial Aplicada a la Empresa

---

# Hoy, en 90 minutos

| Min   | Bloque                          |
| ----- | ------------------------------- |
| 0–15  | Repaso + vuestros casos         |
| 15–35 | Técnicas avanzadas              |
| 35–55 | Caso 2 · Contratos              |
| 55–70 | Caso 3 · Reseñas                |
| 70–85 | Del prompt al flujo             |
| 85–90 | Cierre: chuleta final y recursos |

---
layout: section
number: '01'
minutes: 0–15 min
---

# Repaso + vuestros casos

2 o 3 entregas voluntarias

---
minutes: 0–15
---

# Lo que vimos el martes pasado

- Un prompt es un encargo a un **becario brillante** que no sabe nada de tu empresa.
- **Rol · Contexto · Tarea · Formato · Restricciones · Ejemplos.**
- Contra las alucinaciones: la fuente, «no consta», la cita literal.

<div class="ine-todo mt-6">TODO: 2 o 3 entregas de alumnos (prompt inicial → final → qué cambió)</div>

---
layout: section
number: '02'
minutes: 15–35 min
---

# Técnicas avanzadas

---
minutes: 15–35
---

# Cinco técnicas

<div class="grid grid-cols-3 gap-4 mt-2">
<div class="ine-card ine-card--yellow"><h3>Encarnar roles</h3>Y combinarlos: analista + abogado del diablo.</div>
<div class="ine-card ine-card--yellow"><h3>Dividir en pasos</h3>Un encargo grande, varios pequeños.</div>
<div class="ine-card ine-card--yellow"><h3>Razonar antes de concluir</h3>Primero el análisis, después la respuesta.</div>
<div class="ine-card ine-card--cyan"><h3>Que te pregunte</h3>«Antes de responder, hazme las preguntas que necesites.»</div>
<div class="ine-card ine-card--cyan"><h3>Meta-prompting</h3>Pídele que te ayude a escribir el prompt.</div>
</div>

<div class="ine-todo mt-6">TODO: un ejemplo corto de cada técnica sobre Peluda</div>

---
layout: section
number: '03'
minutes: 35–55 min
---

# Caso 2 · Contratos

Documentos largos: extraer y marcar riesgos

---
minutes: 35–55
---

# Tres contratos con trampa

<div class="grid grid-cols-3 gap-4 mt-2">
<div class="ine-card"><h3>NutriCan Ibérica</h3>Fabricante del pienso.</div>
<div class="ine-card"><h3>Rutas Levante</h3>Transporte y última milla.</div>
<div class="ine-card"><h3>Red VetAmiga</h3>Clínicas veterinarias colaboradoras.</div>
</div>

## El encargo

- **Extrae** los datos clave en una tabla: partes, duración, precio, renovación, penalizaciones.
- **Marca los riesgos** citando la cláusula. Si algo no está, **«no consta»**.

<div class="ine-todo mt-4">TODO: prompt malo → mejor → bueno y captura de la tabla</div>

---
layout: section
number: '04'
minutes: 55–70 min
---

# Caso 3 · Reseñas

La voz de marca, en cada respuesta

---
minutes: 55–70
---

# Guía de estilo + ejemplos → respuestas

<div class="ine-cols">
<div>

## La voz de Peluda

- Cercana, con humor suave, sin tecnicismos.
- Habla a la persona **y** a su mascota, por su nombre.
- Pide perdón primero, explica después.
- En salud no bromea: deriva al veterinario.

</div>
<div>

## Ojo con

- La reseña del **troll**.
- La que trae **datos personales**.
- **Revisión humana** antes de publicar. Siempre.

</div>
</div>

<div class="ine-todo mt-4">TODO: 2 reseñas reales del CMS y sus respuestas</div>

---
layout: section
number: '05'
minutes: 70–85 min
---

# Del prompt al flujo

---
minutes: 70–85
---

# Que no tengas que escribirlo cada vez

<div class="ine-cols">
<div class="ine-card ine-card--yellow">

### Cómo

- Plantillas reutilizables.
- Proyectos de Claude o GPT personalizados.
- Instrucciones fijas. Sin código.

</div>
<div class="ine-card ine-card--cyan">

### Cuándo **no**

- Datos personales.
- Contratos confidenciales en planes gratuitos.
- Decisiones sin revisión humana.

</div>
</div>

<div class="ine-todo mt-6">TODO: captura de un Proyecto «Atención al cliente de Peluda»</div>

---
minutes: 70–85
clicks: 1
---

# La responsabilidad no se delega

<blockquote class="text-xl">

La IA es una herramienta. **La responsabilidad sigue siendo tuya.**

</blockquote>

<div class="flex flex-col gap-2 mt-4">
  <TopicRow title="Una respuesta a un cliente que ofende" tone="warning">tuya</TopicRow>
  <TopicRow title="Un riesgo de un contrato que no viste" tone="warning">tuyo</TopicRow>
  <TopicRow title="Una cifra inventada en un informe" tone="warning">tuya</TopicRow>
</div>

<p v-click class="text-center text-lg italic mt-6">«Copiar y pegar sin revisar no es usar bien la IA: <b>es una negligencia</b>.»</p>

---
minutes: 70–85
---

# Cinco hábitos

<div class="flex flex-col gap-2 mt-2">
  <TopicRow title="Revísalo todo">si llega a un cliente, a un contrato o a dirección, ha pasado antes por tus ojos</TopicRow>
  <TopicRow title="Entiende lo que entregas">si no sabes explicarlo, no lo entregues: pídele que te lo explique</TopicRow>
  <TopicRow title="Itera">la primera respuesta rara vez es la mejor</TopicRow>
  <TopicRow title="Dale contexto">no sabe nada de tu empresa hasta que se lo cuentas</TopicRow>
  <TopicRow title="Comparte lo que funciona">un prompt que acierta, pásaselo a tu equipo</TopicRow>
</div>

---
layout: section
number: '06'
minutes: 85–90 min
---

# Cierre

---
minutes: 85–90
---

# ¿Me va a sustituir la IA?

<div class="flex flex-col gap-2 mt-2">
  <TopicRow title="Cuanto más la usas, más valor tiene tu criterio">el juicio, la intuición del negocio y el contexto aparecen justo cuando la IA se ocupa de lo superficial</TopicRow>
  <TopicRow title="Todos creen que el que está en riesgo es otro equipo">cuando todas las áreas dicen lo mismo a la vez, es un sesgo</TopicRow>
</div>

<div class="ine-card ine-card--yellow mt-6">

### El 88 % de quienes más rinden con IA dicen estar quemados

La IA no reduce el trabajo, lo intensifica: más velocidad → más alcance → más horas. No te estás quedando atrás: la carga es real.

<p class="text-xs mt-1">UC Berkeley · Upwork · HBR, 2026</p>

</div>

<!-- TODO: comprobar la fuente del 88 % antes de la sesión. -->

---
minutes: 85–90
---

# Es un proceso, no un momento

<GriefSpiral class="mt-6" />

<p class="text-center mt-6">No es lineal: es <b>una espiral</b>. Cada vuelta te acerca. Saber en qué fase estás lo acelera.</p>

<p class="text-center text-xs">dev.to/manuartero · <i>Let's talk about grief</i></p>

---
minutes: 85–90
---

# Para llevarte

- La **chuleta final**: plantilla, técnicas avanzadas y checklist.
- Los **datos de Peluda** y el CMS, para practicar cuando quieras.
- Recursos para seguir.

<div class="ine-todo mt-6">TODO: enlaces (chuleta, CMS, recursos)</div>

---
layout: end
---

Taller 1 · Prompt engineering estratégico

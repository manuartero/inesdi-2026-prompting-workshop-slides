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
Clasifica estos tickets.
```

<div class="ine-todo mt-4">TODO: captura del resultado (plan B si falla la demo)</div>

::right::

## Prompt estructurado

```text
Eres responsable de atención al cliente de Peluda…
Contexto: …  Tarea: …  Formato: tabla …
Restricciones: …  Ejemplos: …
```

<div class="ine-todo mt-4">TODO: captura del resultado (plan B si falla la demo)</div>

<!--
Mismos 30 tickets en los dos casos. Que vean el formato inconsistente frente a la tabla.
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
<div class="ine-card ine-card--yellow">

### Qué hace

Comida para perros y gatos **por suscripción**. Cada 4 semanas, en casa.

</div>
<div class="ine-card ine-card--cyan">

### Dónde

España, México, Colombia, Perú y Argentina. ~18.000 suscriptores.

</div>
<div class="ine-card">

### Con quién

**30 personas.** Un equipo pequeño que no da abasto.

</div>
</div>

## Sus tres problemas son nuestros tres casos

- **Tickets:** ~150 al día, primera respuesta en 26 h (objetivo: 4 h).
- **Contratos:** nadie los relee y se renuevan solos.
- **Reseñas:** ~400 al mes, solo se contesta el 30 %.

<!-- Empresa ficticia. Enseñar el CMS «Peluda Admin» un momento. -->

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

# Tres ideas y ya

<div class="grid grid-cols-3 gap-4 mt-6">
<div class="ine-card ine-card--yellow">

### Predice texto plausible

No consulta una base de datos. Escribe lo que *suena* bien.

</div>
<div class="ine-card ine-card--cyan">

### Solo sabe lo que le das

No conoce tu empresa, tus clientes ni tus contratos.

</div>
<div class="ine-card">

### La conversación es su memoria

Lo que hay en el chat es todo lo que tiene para trabajar.

</div>
</div>

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
<div class="ine-card ine-card--yellow"><h3>Rol</h3>Quién es al hacer el trabajo.</div>
<div class="ine-card ine-card--yellow"><h3>Contexto</h3>Lo que sabría un empleado y el becario no.</div>
<div class="ine-card ine-card--yellow"><h3>Tarea</h3>Qué tiene que hacer, con un verbo claro.</div>
<div class="ine-card ine-card--cyan"><h3>Formato</h3>Tabla, lista, columnas, longitud.</div>
<div class="ine-card ine-card--cyan"><h3>Restricciones</h3>Qué no debe hacer.</div>
<div class="ine-card ine-card--cyan"><h3>Ejemplos</h3>Uno o dos casos resueltos.</div>
</div>

<div class="ine-todo mt-6">TODO: el prompt de tickets, con cada pieza resaltada</div>

---
minutes: 25–50
---

# Trucos que siempre funcionan

- **Delimitadores:** separa instrucciones y material (`"""`, `<ticket>`, `---`).
- **Pide la forma:** tabla con columnas fijas, lista numerada, JSON si va a otra herramienta.
- **Uno o dos ejemplos** valen más que un párrafo de explicación.

> CO-STAR, RTF y compañía son variantes de la misma idea. No hace falta memorizarlos.

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

«¿Cuál es la penalización por retraso?» → el modelo **se la inventa**.

<div class="ine-todo mt-4">TODO: captura</div>

</div>
<div>

## Con instrucciones

«Responde solo con el contrato. Si no aparece, di *no consta* y cita la cláusula.» → **no consta**.

<div class="ine-todo mt-4">TODO: captura</div>

</div>
</div>

<!-- Contrato de Rutas Levante o NutriCan: el que tenga la cláusula que falta. -->

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

<div class="ine-todo mt-4">TODO: enlace al CMS y a los tickets para copiar. Pega tu resultado en el chat.</div>

---
layout: section
number: '06'
minutes: 85–90 min
---

# Cierre

---
minutes: 85–90
---

# Para llevarte

<div class="ine-cols">
<div class="ine-card ine-card--yellow">

### La chuleta

Plantilla de prompt + checklist antialucinaciones.

<div class="ine-todo mt-2">TODO: enlace al PDF</div>

</div>
<div class="ine-card ine-card--cyan">

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

---
layout: section
number: '02'
---

# Técnicas avanzadas

Cuando la plantilla ya no basta

---

# Cinco técnicas

<div class="grid grid-cols-3 gap-4 mt-2">
<div class="ine-card ine-card--accent"><h3>Encarnar roles</h3>Y combinarlos: analista + abogado del diablo.</div>
<div class="ine-card ine-card--accent"><h3>Dividir en pasos</h3>Un encargo grande, varios pequeños.</div>
<div class="ine-card ine-card--accent"><h3>Razonar antes de concluir</h3>Primero el análisis, después la respuesta.</div>
<div class="ine-card"><h3>Que te pregunte</h3>«Antes de responder, hazme las preguntas que necesites.»</div>
<div class="ine-card"><h3>Meta-prompting</h3>Pídele que te ayude a escribir el prompt.</div>
</div>

<p class="mt-8">Las usamos todas hoy, en los contratos y en las reseñas.</p>

---

# Encarnar roles, y combinarlos

<div class="grid grid-cols-[1.4fr_1fr] gap-8 mt-2">
<div>

```text
Estamos pensando en salir del contrato con
Rutas Levante. Te adjunto el contrato.

Responde dos veces:
1. Como analista de operaciones: los motivos
   para salir.
2. Como abogado del diablo: todo lo que puede
   salir mal si salimos.

Al final, una tabla con los tres argumentos
más fuertes de cada lado.
```

</div>
<div>
<div class="ine-card ine-card--accent">

### Cuándo

Decisiones con pros y contras.

</div>
<div class="ine-card mt-4">

### Por qué funciona

Con un solo rol, tiende a darte la razón. El abogado del diablo está obligado a llevarte la contraria.

</div>
</div>
</div>

<!-- Enlaza con la práctica de contratos: el abogado del diablo debería encontrar la penalización del Anexo II.6 de Rutas Levante. -->

---

# Dividir en pasos

<div class="grid grid-cols-[1.4fr_1fr] gap-8 mt-2">
<div>

```text
Paso 1 · Extrae los datos clave del contrato
         en una tabla.
         → lo revisas

Paso 2 · Con esa tabla, marca los riesgos
         citando la cláusula.
         → lo revisas

Paso 3 · Resume en 5 líneas para dirección.
```

</div>
<div>
<div class="ine-card ine-card--accent">

### Cuándo

Encargos largos: un contrato, un informe, un análisis.

</div>
<div class="ine-card mt-4">

### Por qué funciona

Cada paso se revisa antes del siguiente. Si algo falla, sabes **dónde**.

</div>
</div>
</div>

---

# Razonar antes de concluir

<div class="grid grid-cols-[1.4fr_1fr] gap-8 mt-2">
<div>

```text
<reseña>…</reseña>

Antes de responder, en <análisis>:
- ¿Qué situación es? (elogio, retraso,
  salud, troll…)
- ¿Qué tono pide la guía de voz?
- ¿Qué país es y qué trato toca
  (tú, usted, vos)?

Después, en <respuesta>, la respuesta.
```

</div>
<div>
<div class="ine-card ine-card--accent">

### Cuándo

Si la respuesta depende de entender bien el caso primero.

</div>
<div class="ine-card mt-4">

### Por qué funciona

El modelo escribe palabra a palabra: lo que ya ha escrito guía lo que viene después. Y el análisis **lo puedes revisar tú**.

</div>
</div>
</div>

<!-- Los modelos «con razonamiento» ya piensan por dentro antes de contestar. Pedir el análisis por escrito sigue sirviendo: lo ves y puedes corregirlo. -->

---

# Que te ayude a escribir el prompt

<div class="grid grid-cols-2 gap-6 mt-2">
<div>

## Que te pregunte

```text
Quiero avisar a los clientes de Argentina
de una subida de precios.

Antes de escribir nada, hazme las
preguntas que necesites, de una en una.
```

<p class="text-sm mt-2">Te descubre lo que no habías pensado: cuánto sube, desde cuándo, si hay algo a cambio.</p>

</div>
<div>

## Meta-prompting

```text
Te adjunto nuestra guía de voz.

Escríbeme un prompt para que un asistente
responda reseñas siguiendo esta guía.
Usa etiquetas y deja un hueco para pegar
la reseña.
```

<p class="text-sm mt-2">Un buen punto de partida. El prompt que te da <b>también hay que probarlo</b>.</p>

</div>
</div>

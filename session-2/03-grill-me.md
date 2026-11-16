---
layout: section
number: '03'
kicker: 'Grill me'
---

# Grill me

Que te pregunte antes de hacer nada

---

# Lo que no le cuentas, se lo inventa

<div class="grid grid-cols-[1.3fr_1fr] gap-8 mt-2">
<div>

<div class="ine-tile ine-tile--accent">
  <span class="ine-tile__icon"><span class="i-ph-chats-circle-fill" /></span>
  <h3>La frase</h3>
  <p class="text-base">«Antes de hacer nada, <b>hazme preguntas, de una en una</b>, hasta que tengas claro lo que necesito.»</p>
</div>

</div>
<div>
<div class="ine-card ine-card--accent">

### Por qué funciona

Tú sabes cosas que no has escrito. Si no se las das, rellena el hueco con algo plausible.

</div>
<div class="ine-card mt-4">

### Cuándo

Cuando no sabes bien qué contexto darle. Él te lo pide.

</div>
</div>
</div>

<!--
«Grill me» = «sométeme a un interrogatorio». Viene de una skill de Matt Pocock que se hizo viral en 2026: un entrevistador que no para hasta que los dos entendéis lo mismo.
Enlaza con la sesión 1: a Lucía no le faltaban instrucciones, le faltaban datos. Aquí es el modelo el que te pide los datos.
«De una en una» importa: si no, te suelta quince preguntas de golpe y no contestas ninguna bien.
-->

---
clicks: 1
---

# Demo: subimos precios en Argentina

<div class="grid grid-cols-2 gap-8 mt-2">
<div>

## A · Directo

```text
Escribe un correo a los clientes de
Argentina para avisar de una subida
de precios.
```

## B · + Grill me

```text
Escribe un correo a los clientes de
Argentina para avisar de una subida
de precios.

Antes de escribir nada, hazme preguntas,
de una en una, hasta que tengas claro
lo que necesito.
```

</div>
<div>

## Lo que preguntó B

<div class="topic-list" v-click>
  <TopicRow title="1" icon="i-ph-buildings-fill">¿qué empresa eres y qué sube de precio?</TopicRow>
  <TopicRow title="2" icon="i-ph-percent-fill">¿cuánto sube y desde qué fecha?</TopicRow>
  <TopicRow title="3" icon="i-ph-question-fill">¿quieres explicar el motivo? ¿Cuál?</TopicRow>
  <TopicRow title="4" icon="i-ph-gift-fill">¿ofreces algo: pausar, cambiar de plan, cancelar, un descuento?</TopicRow>
</div>

</div>
</div>

<!--
Sin contexto, a propósito: ni siquiera le decimos que somos Peluda. Pregunta: «¿Qué creéis que hará A?».
Lo que contestamos a B: Peluda, comida para mascotas por suscripción; un 9 % desde el próximo cobro; suben los costes de producción; nada a cambio, pero se puede cambiar de plan o darse de baja gratis desde la app.
Prompts y resultado en demos/sesion-2/02-grill-me.md.
-->

---

# Una plantilla contra un correo

<div class="grid grid-cols-2 gap-8">
<div>

## A · Directo

<div class="relative inline-block mt-1">
  <img src="/captures/s2-grill-me-a.png" style="height: 215px" class="border border-gray-300" alt="Correo A: una plantilla genérica con huecos, de usted" />
  <span class="ine-hl" style="left: 5%; top: 20.6%; width: 86%; height: 6.4%" />
  <span class="ine-hl" style="left: 5%; top: 29.6%; width: 86%; height: 3.6%" />
</div>

<p class="mt-2" style="font-size: 0.8rem; line-height: 1.4">Una plantilla de manual: <b>[X] %</b>, <b>[motivo]</b>, «Estimado/a», de usted. No sabe ni qué vendemos.</p>

</div>
<div>

## B · + Grill me

<div class="relative inline-block mt-1">
  <img src="/captures/s2-grill-me-b.png" style="height: 215px" class="border border-gray-300" alt="Correo B: el correo de Peluda, con el 9 %, de vos y con las salidas" />
  <span class="ine-hl" style="left: 5%; top: 24%; width: 88%; height: 6%" />
  <span class="ine-hl" style="left: 5%; top: 49.4%; width: 88%; height: 3.2%" />
</div>

<p class="mt-2" style="font-size: 0.8rem; line-height: 1.4">El correo de Peluda: <b>9 % desde el próximo cobro</b>, de vos, y con salidas: cambiar de plan o darse de baja.</p>

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
Resultado real (16/11).
A no se inventa las cifras (bien: deja huecos), pero entrega una plantilla genérica de empresa cualquiera: «Estimado/a», de usted, «[productos/servicios]», «[motivo: aumento de costos, inflación…]». Hasta te dice que usó usted y que, si sois más cercanos, se puede pasar a vos.
B hizo cuatro preguntas, y con cuatro respuestas el correo ya es de Peluda: el 9 %, el próximo cobro, el motivo, las salidas, la mascota. Vosea y usa «costos» sin que se lo pidiéramos.
Lo que no preguntó: el trato. Lo adivinó bien, pero lo adivinó. Eso es lo que resuelve una skill con la guía de voz (bloque 5).
-->

---

# Tu turno: grill me

<div class="grid grid-cols-[1.3fr_1fr] gap-8 mt-2">
<div>

<div class="ine-tile">
  <span class="ine-tile__icon"><span class="i-ph-briefcase-fill" /></span>
  <h3>Tu tarea real</h3>
  <p>La que trajiste para hoy. Si no trajiste ninguna: <i>«avisa a los clientes del problema con el pienso nuevo»</i>.</p>
  <p class="ine-tile__remedy"><b>Tu tarea:</b> empieza con grill me y contesta a sus preguntas.</p>
</div>

</div>
<div class="topic-list">
  <TopicRow title="1" icon="i-ph-chat-circle-text-fill">pide la tarea + «hazme preguntas, de una en una»</TopicRow>
  <TopicRow title="2" icon="i-ph-list-numbers-fill">contesta hasta que diga que lo tiene claro</TopicRow>
  <TopicRow title="3" icon="i-ph-paper-plane-tilt-fill">pega en el chat de la clase la pregunta que no se te había ocurrido</TopicRow>
</div>
</div>

<!-- El pienso nuevo: el hilo del perro que vomita (tickets 0004, 0015, 0063, 0145). Buenas preguntas: ¿está confirmado que es el pienso?, ¿a quién se avisa (solo a quien compró ese lote)?, ¿qué les pedimos (el número de lote, ir al veterinario)?, ¿qué ofrecemos? -->

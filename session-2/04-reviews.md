---
layout: section
number: '04'
---

# Caso 3 · Reseñas

La voz de marca, en cada respuesta

---

# La voz de Peluda

<div class="ine-cols">
<div>

## En una frase

Como **una vecina que sabe mucho de mascotas**: cercana, con humor suave, sin tecnicismos.

- Por su nombre: el de la persona **y** el de su mascota.
- Primero perdón, luego explicación.
- Cada país, su trato: tú, usted, vos.
- En salud no bromea: veterinario en la primera frase.

</div>
<div>

## Ojo con

- La reseña del **troll**.
- La que trae **datos personales**.
- **Revisión humana** antes de publicar. Siempre.

<p class="text-sm mt-6" style="color: var(--ine-muted)">En el CMS: <b>Marca</b> → «Copiar para el prompt». Una página.</p>

</div>
</div>

---

# El prompt de las reseñas

<div class="grid grid-cols-[1.5fr_1fr] gap-8 mt-2">
<div>

```text
<guia_de_voz>[pega la guía de voz]</guia_de_voz>

<ejemplos>
[dos respuestas ya publicadas que nos gustan]
</ejemplos>

<reseña>[pega la reseña]</reseña>

<goal>
Primero, en <análisis>: situación, tono y trato.
Después, en <respuesta>: la respuesta.
</goal>

<restricciones>
- Nunca repitas datos personales de la reseña.
- No diagnostiques. No prometas lo que no
  puedas comprobar.
</restricciones>
```

</div>
<div class="topic-list">
  <TopicRow title="Guía" icon="i-ph-book-open-fill">el tono, por escrito</TopicRow>
  <TopicRow title="Ejemplos" icon="i-ph-lightbulb-fill">el tono, en la práctica: Francisco e Inma</TopicRow>
  <TopicRow title="Análisis" icon="i-ph-brain-fill">razonar antes de concluir</TopicRow>
</div>
</div>

<!--
Los dos ejemplos son respuestas ya publicadas en el CMS: Francisco (elogio, Lur) e Inma (retraso: perdón primero y algo concreto).
Si alguien pregunta de dónde sale el prompt: se puede pedir con meta-prompting y luego ajustarlo.
Prompt completo en demos/sesion-2/02-resenas.md.
-->

---

# Demo: dos reseñas difíciles

<div class="grid grid-cols-2 gap-6 mt-2">
<div class="ine-tile">
  <span class="ine-tile__icon"><span class="i-ph-first-aid-kit-fill" /></span>
  <h3>Rocío · 2 estrellas</h3>
  <p class="ine-tile__example">«Desde que cambiaron el pienso mi perra vomita casi todos los días. Antes estaba perfecta. Ya la he llevado al veterinario. ¿A alguien más le pasa?»</p>
  <p class="ine-tile__remedy">Veterinario en la primera frase, el lote por privado, <b>sin diagnosticar</b>. Y avisar a Producto: es el mismo pienso de los tickets.</p>
</div>
<div class="ine-tile">
  <span class="ine-tile__icon"><span class="i-ph-identification-card-fill" /></span>
  <h3>Patricia · 2 estrellas · México</h3>
  <p class="ine-tile__example">«Me llegaron las croquetas del gato. Me cobraron con mi tarjeta terminación 4417. Llámenme al +52 222… o vengan a Calle 5 de Mayo…»</p>
  <p class="ine-tile__remedy">Ni tarjeta, ni teléfono, ni dirección en la respuesta: <b>a un canal privado</b>. Y pedir ocultar la reseña.</p>
</div>
</div>

<div class="ine-todo mt-4">TODO: capturas de las dos respuestas (s2-resenas-rocio.png, s2-resenas-patricia.png)</div>

<!--
Rocío: cierra el hilo del perro que vomita (tickets 0004, 0015, 0063, 0145 y la cláusula 5.4 de NutriCan: 48 horas). Responder bien la reseña no basta: alguien tiene que avisar a Producto y al fabricante.
Patricia: México → tú, cálido y algo más formal. El fallo típico es repetir el teléfono o la dirección para «confirmar».
-->

---

# Antes de publicar, una persona revisa

<div class="topic-list mt-2">
  <TopicRow title="Nombre y trato" icon="i-ph-user-fill">el de la persona y el de su mascota; tú, usted o vos según el país</TopicRow>
  <TopicRow title="Salud" icon="i-ph-first-aid-kit-fill">veterinario en la primera frase; ningún diagnóstico</TopicRow>
  <TopicRow title="Datos personales" icon="i-ph-lock-fill">ninguno repetido; lo privado, por privado</TopicRow>
  <TopicRow title="Promesas" icon="i-ph-handshake-fill">nada que no podamos cumplir: ni plazos, ni descuentos</TopicRow>
  <TopicRow title="Algo más que contestar" icon="i-ph-arrow-bend-up-right-fill">¿hay que avisar a alguien? ¿abrir un ticket?</TopicRow>
  <TopicRow title="¿La firmarías tú?" tone="warning" icon="i-ph-signature-fill">si no, no se publica</TopicRow>
</div>

---

# Tu turno: dos reseñas más

<div class="grid grid-cols-2 gap-6 mt-2">
<div class="ine-tile">
  <span class="ine-tile__icon"><span class="i-ph-smiley-angry-fill" /></span>
  <h3>Kike_88 · 1 estrella</h3>
  <p class="ine-tile__example">«Pienso del súper metido en una bolsa bonita y a 45 pavos. Una estafa para pijos…»</p>
</div>
<div class="ine-tile">
  <span class="ine-tile__icon"><span class="i-ph-heart-fill" /></span>
  <h3>Pilar · 5 estrellas</h3>
  <p class="ine-tile__example">«Nala nos dejó con 16 años. Comió Peluda desde el primer mes… Gracias a todo el equipo.»</p>
</div>
</div>

<p class="mt-6">En el CMS: <b>Reseñas</b> → «Copiar para el prompt». Prueba el prompt y pega en el chat de la clase <b>la respuesta que publicarías</b>.</p>

<!--
Kike (troll): una sola respuesta, breve y educada, sin entrar al trapo. Muchos modelos contestan con un argumentario a la defensiva (ingredientes, precio por día…): eso es entrar al trapo.
Pilar: cinco estrellas, pero es un duelo. Respetuosa, sin emojis, sin vender nada y confirmando que no habrá más envíos ni cobros (va con el ticket 0024).
-->

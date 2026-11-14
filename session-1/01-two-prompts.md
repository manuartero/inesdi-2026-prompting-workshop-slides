---
layout: section
number: '01'
---

# La misma tarea, 2x prompts diferentes

Demo en directo antes de explicar nada

---
layout: two-cols
---

# Prompt básico vs. prompt estructurado

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

# El prompt de una línea, revisado contra el sistema

<div class="topic-list mt-1">
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

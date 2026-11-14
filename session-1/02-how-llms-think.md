---
layout: section
number: '02'
---

# Cómo «piensa» un LLM

Solo lo que explica su comportamiento

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

> Con los LLM estamos a mitad de camino. Las próximas slides marcan el techo.

<!--
Magneto en los cómics de los 70–80 frente al Magneto que dirige la escuela (X-Men, 1993).
Imágenes de Marvel: uso ilustrativo en clase.
-->

---

# Un JPEG borroso de internet

<div class="grid grid-cols-2 gap-8 mt-2 items-center">
<PretrainingCompression />
<div class="topic-list">
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

# Las conversaciones largas se degradan

<div class="topic-list mt-2">
  <TopicRow title="Su atención es limitada">cuanto más larga la conversación, más se reparte</TopicRow>
  <TopicRow title="Lo reciente se ve nítido">lo del principio se vuelve borroso</TopicRow>
</div>

<div class="mt-10">
  <ContextWindowZones />
</div>

<p class="text-center mt-4">Que el chat admita más texto no amplía la zona lúcida: solo añade <b>zona torpe</b>.</p>

---

# El modelo no recuerda: la aplicación toma notas

<div class="topic-list mt-2">
  <TopicRow title="El modelo">no guarda nada entre chats: solo ve lo que le llega en cada conversación</TopicRow>
  <TopicRow title="La conversación">su memoria de trabajo: lo que hay en el chat y lo que adjuntas</TopicRow>
  <TopicRow title="El proyecto">instrucciones y ficheros que la aplicación añade a cada chat del proyecto</TopicRow>
  <TopicRow title="Tú (el usuario)">la aplicación va tomando notas de ti entre chats: a qué te dedicas, cómo te gusta que responda</TopicRow>
  <TopicRow title="Congelado en el tiempo" tone="warning">sabe lo que había hasta su entrenamiento; lo de después, solo si lo busca en la web o se lo das</TopicRow>
</div>

<p class="mt-5 text-[0.95rem]">Claude y ChatGPT son el modelo más un programa alrededor que gestiona esa memoria: el <span class="ine-mark">harness</span>.</p>

<!--
Antes se decía «cada chat empieza de cero». Hoy el modelo sigue sin memoria, pero la aplicación (el «harness») la simula por capas: conversación, proyecto y memoria del usuario.
- Proyectos: Claude Projects, ChatGPT Projects. Se ve en la sesión 2 («Del prompt al flujo»).
- Memoria del usuario: se puede ver y borrar en los ajustes de cada app. Que lo comprueben: a veces guarda cosas que no queríais.
- Moraleja práctica: lo importante para la tarea, ponlo tú en el chat o en el proyecto; no cuentes con que «ya lo sabe».
-->

---

# Los límites

<div class="topic-list mt-2">
  <TopicRow title="Memoria borrosa" icon="i-ph-file-jpg-fill">es un JPEG borroso de internet</TopicRow>
  <TopicRow title="Atención limitada" icon="i-ph-flashlight-fill">las conversaciones largas se degradan</TopicRow>
  <TopicRow title="Memoria por capas" icon="i-ph-notepad-fill">recuerda notas, no todo</TopicRow>
  <TopicRow title="Fecha de corte" icon="i-ph-calendar-x-fill">congelado en el tiempo</TopicRow>
</div>

<blockquote class="mt-6 text-lg">

Los cuatro empujan hacia lo mismo: **pon en la conversación lo que importa, y solo lo que importa.**

</blockquote>

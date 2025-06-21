---
layout: default
title: Equipo
---

<h1>Equipo</h1>
<div class="equipo">
  {% for persona in site.data.equipo %}
    <div class="tarjeta" onclick="mostrarModal('{{ forloop.index0 }}')">
      <img src="{{ persona.imagen }}" alt="{{ persona.nombre }}" style="width:150px;">
      <h3>{{ persona.nombre }}</h3>
    </div>
  {% endfor %}
</div>

<div id="modal" class="modal" style="display:none;">
  <div class="contenido-modal" id="contenido-modal">
    <!-- Aquí se insertará dinámicamente -->
  </div>
</div>

<script>
  const data = {{ site.data.equipo | jsonify }};

  function mostrarModal(index) {
    const persona = data[index];
    const modal = document.getElementById("modal");
    const contenido = document.getElementById("contenido-modal");

    contenido.innerHTML = `
      <h2>${persona.nombre}</h2>
      <img src="${persona.imagen}" style="width:100px;">
      <p>${persona.descripcion}</p>
      <a href="${persona.twitter}" target="_blank">Twitter</a> |
      <a href="${persona.youtube}" target="_blank">YouTube</a> |
      <a href="${persona.github}" target="_blank">GitHub</a>
      <br><br><button onclick="cerrarModal()">Cerrar</button>
    `;
    modal.style.display = "block";
  }

  function cerrarModal() {
    document.getElementById("modal").style.display = "none";
  }
</script>

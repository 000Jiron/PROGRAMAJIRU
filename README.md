# PROGRAMAJIRU
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Editor HTML Móvil - Estilo Elegante</title>
  <style>
    :root {
      --color-oro: #FFD700;
      --color-oro-suave: #F0E68C;
      --color-negro-fondo: #0A0A0A;
      --color-negro-interfaz: #1A1A1A;
      --color-negro-texto: #050505;
      --color-borde-dorado: #B8860B;
    }

    body {
      margin: 0;
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      display: flex;
      flex-direction: column;
      min-height: 100vh;
      background-color: var(--color-negro-fondo);
      color: var(--color-oro-suave);
      background-image:
        linear-gradient(45deg, var(--color-borde-dorado) 1.5px, transparent 1.5px),
        linear-gradient(135deg, var(--color-borde-dorado) 1.5px, transparent 1.5px);
      background-size: 60px 60px;
      background-position: 0 0;
      perspective: 1000px;
    }

    header {
      background: var(--color-negro-interfaz);
      color: var(--color-oro);
      padding: 1rem;
      text-align: center;
      font-size: 1.5em;
      font-weight: bold;
      border-bottom: 3px solid var(--color-oro);
      box-shadow: 0 4px 15px rgba(255, 215, 0, 0.2);
      text-transform: uppercase;
      letter-spacing: 1.5px;
    }

    #controls {
      display: flex;
      flex-wrap: wrap;
      gap: 0.7rem;
      padding: 0.8rem 1rem;
      background: rgba(10, 10, 10, 0.85);
      backdrop-filter: blur(5px);
      border-bottom: 2px solid var(--color-borde-dorado);
      box-shadow: 0 5px 20px rgba(0, 0, 0, 0.5);
      justify-content: center;
      align-items: center;
      position: relative;
      transform-style: preserve-3d;
    }

    input, select, button {
      padding: 0.7rem 1rem;
      font-size: 0.9rem;
      background-color: var(--color-negro-interfaz);
      color: var(--color-oro);
      border: 1.5px solid var(--color-borde-dorado);
      border-radius: 6px;
      cursor: pointer;
      transition: all 0.3s ease;
      box-shadow: 0 2px 5px rgba(0, 0, 0, 0.3);
      outline: none;
      flex-grow: 1;
      flex-basis: auto;
    }
    input[type="text"], select {
        flex-grow: 2;
        min-width: 150px;
    }


    input::placeholder {
      color: var(--color-oro-suave);
      opacity: 0.7;
    }

    input:focus, select:focus, button:focus {
      border-color: var(--color-oro);
      box-shadow: 0 0 10px rgba(255, 215, 0, 0.5);
    }

    button:hover {
      background-color: var(--color-oro);
      color: var(--color-negro-interfaz);
      border-color: var(--color-oro);
      box-shadow: 0 4px 12px rgba(255, 215, 0, 0.4);
      transform: translateY(-2px);
    }

    button:active {
      transform: translateY(0px);
      box-shadow: 0 2px 5px rgba(255, 215, 0, 0.3);
    }

    select {
      appearance: none;
      background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='16' height='16' fill='%23FFD700' viewBox='0 0 16 16'%3E%3Cpath fill-rule='evenodd' d='M1.646 4.646a.5.5 0 0 1 .708 0L8 10.293l5.646-5.647a.5.5 0 0 1 .708.708l-6 6a.5.5 0 0 1-.708 0l-6-6a.5.5 0 0 1 0-.708z'/%3E%3C/svg%3E");
      background-repeat: no-repeat;
      background-position: right 0.7rem center;
      padding-right: 2.5rem;
    }

    .editor-container {
      display: flex;
      flex-direction: column;
      flex-grow: 1;
      overflow: hidden;
      padding: 15px;
      gap: 15px;
      perspective: 800px;
      transform-style: preserve-3d;
    }

    textarea, iframe {
      flex: 1;
      min-height: 200px;
      padding: 15px;
      font-family: 'Consolas', 'Courier New', monospace;
      font-size: 0.9rem;
      border: 2px solid var(--color-borde-dorado);
      outline: none;
      resize: none;
      box-shadow: 0 0 25px rgba(0, 0, 0, 0.7) inset;
      transform: translateZ(10px);
      border-radius: 8px;
      width: 100%;
      box-sizing: border-box;
    }

    textarea {
      background-color: #1E1E1E;
      color: #D4D4D4;
    }

    iframe {
      background-color: #fff;
    }

    .hidden {
      display: none !important;
    }

    ::-webkit-scrollbar {
      width: 8px;
      height: 8px;
    }
    ::-webkit-scrollbar-track {
      background: var(--color-negro-interfaz);
      border-radius: 4px;
    }
    ::-webkit-scrollbar-thumb {
      background: var(--color-oro);
      border-radius: 4px;
    }
    ::-webkit-scrollbar-thumb:hover {
      background: var(--color-oro-suave);
    }

    @media (min-width: 768px) {
      header {
        padding: 1.2rem;
        font-size: 1.8em;
        letter-spacing: 2px;
      }

      #controls {
        padding: 1rem 1.5rem;
        gap: 0.8rem;
        justify-content: flex-start;
      }
      input, select, button {
        font-size: 0.95rem;
        flex-grow: 0;
      }
      input[type="text"], select {
        flex-grow: 1;
        min-width: 200px;
      }

      .editor-container {
        flex-direction: row;
      }

      textarea, iframe {
        font-size: 1rem;
        flex-basis: 0;
        min-height: 300px;
      }
    }

    @media (max-width: 420px) {
      header {
        font-size: 1.3em;
        padding: 0.8rem;
        letter-spacing: 1px;
      }

      #controls {
        padding: 0.6rem 0.5rem;
        gap: 0.5rem;
      }

      input, select, button {
        font-size: 0.85rem;
        padding: 0.6rem 0.8rem;
      }
      #saveName, #savedCodes {
         flex-basis: calc(100% - 1rem); /* Ocupa toda la línea menos el gap */
         flex-grow: 1;
      }
      /* Ajuste para que los botones de acción principal (Visualizar, Ejecutar, Código) tengan más prominencia si es necesario */
      #controls button.action-main {
          flex-basis: calc(33% - 0.8rem); /* Ejemplo para 3 botones en una línea */
      }
       /* Para los demás botones como guardar, cargar, eliminar */
      #controls button:not(.action-main) {
        flex-basis: calc(50% - 0.75rem);
      }
      /* Si #saveName y #savedCodes ocupan toda la línea, los botones se reacomodarán debajo */


      textarea, iframe {
        font-size: 0.85rem;
        min-height: 150px;
      }

      ::-webkit-scrollbar {
        width: 6px;
        height: 6px;
      }
    }
    /* Específico para pantallas muy pequeñas, asegurar que botones importantes no se corten tanto */
    @media (max-width: 360px) {
        #controls button.action-main, #controls button:not(.action-main) {
            flex-basis: calc(100% - 0.5rem); /* Un botón por línea */
        }
    }


  </style>
</head>
<body>
  <header>EDITOR HTML SOCIEDAD ANONIMA</header>
  <div id="controls">
    <button onclick="updatePreview()" title="Visualizar resultado en la página" class="action-main">Visualizar</button>
    <button onclick="openInNewWindow()" title="Ejecutar código en una nueva ventana" class="action-main">Ejecutar</button>
    <button onclick="toggleEditor()" title="Mostrar/Ocultar editor de código" class="action-main">Código</button>
    <input id="saveName" type="text" placeholder="Nombre para guardar...">
    <button onclick="saveCode()" title="Guardar código actual">Guardar</button>
    <select id="savedCodes" onchange="loadCode()" title="Cargar código guardado">
      <option value="">Cargar código...</option>
    </select>
    <button onclick="deleteCode()" title="Eliminar código seleccionado">Eliminar</button>
  </div>
  <div class="editor-container">
    <textarea id="editor" placeholder="ESCRIBE TU CÓDIGO HTML AQUÍ..."></textarea>
    <iframe id="preview"></iframe>
  </div>

  <script>
    const editor = document.getElementById('editor');
    const preview = document.getElementById('preview');
    const saveName = document.getElementById('saveName');
    const savedCodes = document.getElementById('savedCodes');

    function updatePreview() {
      const content = editor.value;
      preview.srcdoc = content;
    }

    function openInNewWindow() {
      const content = editor.value;
      if (content.trim() === "") {
        alert("No hay código para ejecutar en una nueva ventana.");
        return;
      }
      try {
        const newWindow = window.open("", "_blank");
        if (newWindow) {
          newWindow.document.open();
          newWindow.document.write(content);
          newWindow.document.close();
          newWindow.document.title = "Resultado del Código - Vista Funcional";
        } else {
          alert("No se pudo abrir la nueva ventana. Por favor, revisa si tu navegador está bloqueando las ventanas emergentes para este sitio.");
        }
      } catch (e) {
        console.error("Error al abrir la nueva ventana:", e);
        alert("Ocurrió un error al intentar abrir la nueva ventana. Revisa la consola para más detalles.");
      }
    }

    function toggleEditor() {
      editor.classList.toggle('hidden');
    }

    function saveCode() {
      const name = saveName.value.trim();
      if (name) {
        const key = 'code_' + name;
        if (localStorage.getItem(key)) {
          const confirmOverwrite = confirm(`Ya existe un código llamado "${name}". ¿Deseas sobrescribirlo?`);
          if (!confirmOverwrite) return;
        }
        localStorage.setItem(key, editor.value);
        updateSavedCodes();
        saveName.value = '';
        alert(`Código "${name}" guardado.`);
      } else {
        alert("Por favor, ingresa un nombre para guardar el código.");
      }
    }

    function loadCode() {
      const name = savedCodes.value;
      if (name) {
        editor.value = localStorage.getItem('code_' + name);
        updatePreview(); // Al cargar, solo actualiza la vista previa en el iframe
        if (editor.classList.contains('hidden')) {
          editor.classList.remove('hidden');
        }
        alert(`Código "${name}" cargado.`);
      }
    }

    function deleteCode() {
      const name = savedCodes.value;
      if (name && confirm(`¿Seguro que deseas eliminar el código "${name}"?`)) {
        localStorage.removeItem('code_' + name);
        updateSavedCodes();
        editor.value = '';
        preview.srcdoc = '';
        alert(`Código "${name}" eliminado.`);
      } else if (!name) {
        alert("Selecciona un código para eliminar.");
      }
    }

    function updateSavedCodes() {
      savedCodes.innerHTML = '<option value="">Cargar código...</option>';
      const keys = Object.keys(localStorage);
      keys.sort(); 
      for (let i = 0; i < keys.length; i++) {
        const key = keys[i];
        if (key.startsWith('code_')) {
          const name = key.replace('code_', '');
          const option = document.createElement('option');
          option.value = name;
          option.textContent = name;
          savedCodes.appendChild(option);
        }
      }
    }

    // Inicialización
    updateSavedCodes();
    // Al cargar la página, mostrar la vista previa del código actual en el editor (si hay alguno)
    updatePreview(); 
    if (editor.classList.contains('hidden')) {
       editor.classList.remove('hidden');
    }
  </script>
</body>
</html>

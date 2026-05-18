# UniMentor — Plataforma de Mentorías Universitarias

Prototipo de alta fidelidad de una plataforma EdTech que conecta a estudiantes
de primeros semestres con mentores de semestres superiores, al estilo
**Uber matching + chat académico**. El objetivo es facilitar la adaptación
universitaria, reducir la deserción y crear comunidad colaborativa.

Está construido en **un solo archivo `index.html`** (React + Tailwind vía CDN).
No requiere instalar nada ni compilar.

---

## 1. Cómo ejecutarlo

No se necesita Node, Python ni programas. Solo un navegador
(Chrome / Edge / Firefox) e internet (la primera vez, para cargar los estilos).

### Opción A — Descargar y abrir (la más fácil)

1. Abre el archivo `index.html` en este repositorio.
2. Haz clic en el botón **"Download raw file"** (ícono ⬇️ arriba a la
   derecha del recuadro de código).
3. Ve a tu carpeta de **Descargas** y haz **doble clic** en `index.html`.
4. Se abre solo en el navegador. ¡Listo!

### Opción B — Descargar todo el proyecto

1. Botón verde **"Code"** → **"Download ZIP"**.
2. Clic derecho al ZIP → **"Extraer todo"**.
3. Doble clic en `index.html`.

### Opción C — Clonar con Git (si sabes usar la terminal)

```bash
git clone https://github.com/JoSker51/unimentor.git
cd unimentor
# Abre index.html con doble clic, o sirve la carpeta:
python -m http.server 8000   # luego abre http://localhost:8000
```

### Si no se ve bien

- Necesita internet la primera vez (carga estilos desde la web).
- Si sale en blanco: espera 5–10 segundos y refresca con **F5**.
- Mejor en Chrome o Edge, en pantalla de computador o tablet.

---

## 2. Cómo usar la aplicación

1. En el login, elige un rol: **"Busco ayuda"** (estudiante) o
   **"Quiero ser mentor"**. Los campos vienen con datos de ejemplo.
2. Clic en **Iniciar sesión**.
3. Navega con el **menú de la izquierda** (en tablet/móvil, con el botón ☰).

**Recorrido recomendado para una demo completa:**

1. Entra como **estudiante** → *Solicitar ayuda* → cambia la materia y envía.
2. Verás la pantalla de **matching** usando esa materia → *Aceptar mentor* →
   "esperando confirmación" → **¡Match!** → *Abrir chat*.
3. En el **chat**: escribe un mensaje, **adjunta un archivo**, activa
   **compartir pantalla**, y pulsa **Finalizar** → califica con estrellas.
4. La sesión queda **guardada y resaltada** en *Historial*.
5. *Cerrar sesión* → entra como **mentor** → acepta/rechaza solicitudes,
   revisa incentivos y disponibilidad.

---

## 3. Funcionalidades

### Rol Estudiante (busca ayuda)
- **Dashboard** con métricas, mentores recomendados y próxima sesión.
- **Formulario de solicitud**: materia, tema, descripción, nivel de
  urgencia y horario (con validación).
- **Matching tipo Uber**: búsqueda animada → tarjeta de mentor con foto,
  semestre, especialidad, rating, tiempo de respuesta y estado online →
  *Aceptar / Saltar / Ver perfil* → confirmación del mentor → match.
- **Chat de mentoría**: mensajes en tiempo real, adjuntar archivos,
  compartir pantalla, cronómetro de sesión, panel lateral (temas tratados,
  recursos, ejercicios) y modal de **finalizar + valorar**.
- **Perfil completo del mentor**: carrera, semestre, rating, horas
  ayudando, logros, incentivos e historial.
- **Historial** de sesiones y **perfil propio** con progreso por materia.

### Rol Mentor (estudiante avanzado)
- **Dashboard** con estadísticas, sesión activa y progreso de incentivos.
- **Solicitudes en tiempo real**: nombre, materia, urgencia, tiempo desde
  la solicitud, con **Aceptar / Rechazar** funcionales.
- **Sistema de incentivos**: horas de servicio social, puntos, racha,
  barra de progreso y recompensas desbloqueables (certificados, bonos,
  beneficios universitarios).
- **Configurar disponibilidad**: estado, días, franja horaria y materias.

### Transversal
- Login/Register con selección de rol.
- Notificaciones (toasts) en cada acción.
- Diseño responsive (desktop y tablet) con sidebar colapsable.
- Estética SaaS: azul SAP (#0A6ED1), tarjetas limpias, sombras suaves,
  animaciones, indicadores online.

---

## 4. Cómo cumple cada criterio de la rúbrica

> **Prototipo de alta fidelidad (20%)** — nivel esperado: *"alcanza un nivel
> profesional y altamente realista, simula de manera convincente la
> experiencia real, incorpora detalles funcionales, visuales y de
> interacción, y demuestra madurez conceptual, técnica y estratégica."*

| Lo que pide la rúbrica | Cómo lo cumple el prototipo |
|---|---|
| **Nivel profesional y altamente realista** | UI tipo SaaS (SAP Fiori / Teams / Slack): sidebar, topbar, tarjetas, tipografía Inter, paleta corporativa, sombras y animaciones consistentes en las 11 pantallas. |
| **Simula de manera convincente la experiencia real** | Flujo de punta a punta con estado real: la solicitud creada **alimenta** el matching, el chat y el historial. El matching imita a Uber (búsqueda → confirmación mutua → match). |
| **Detalles funcionales** | Acciones reales, no decorativas: enviar solicitud con validación, aceptar/rechazar elimina tarjetas y actualiza contadores, finalizar sesión guarda la sesión calificada en el historial, toggles y selección de materias funcionales. |
| **Detalles de interacción** | Adjuntar archivo inserta el archivo en el chat, compartir pantalla activa un banner, el chat responde, notificaciones toast, estados vacíos, contador de mentores saltados, modales de perfil y de valoración. |
| **Detalles visuales** | Animaciones de entrada, anillo pulsante en búsqueda, spinner de espera, avatares con estado online, barras de progreso, badges y jerarquía visual cuidada. |
| **Coherencia visual, funcional y narrativa** | Mismo sistema de diseño en todo; los incentivos del mentor son coherentes con las horas ganadas en sesiones reales; narrativa de bienestar y reducción de deserción presente en login, dashboards y tips. |
| **Madurez conceptual y estratégica** | Modelo de dos roles con incentivos (servicio social, puntos, becas) que resuelve el problema real: adaptación universitaria, retención y comunidad colaborativa. |
| **Madurez técnica** | Arquitectura de componentes con estado global (React Context), enrutado por roles, datos de ejemplo realistas y diseño responsive — todo sin dependencias que instalar. |
| **Responsive (desktop y tablet)** | Sidebar colapsable con menú ☰ y overlay, grids que se reacomodan, tablas con scroll horizontal y cabeceras que envuelven. |

---

## 5. Pantallas incluidas

Login/Register · Dashboard estudiante · Formulario de solicitud · Matching
mentor-estudiante · Chat de mentoría · Perfil de mentor · Dashboard mentor ·
Solicitudes en tiempo real · Sistema de incentivos · Historial · Disponibilidad
· Configuración de perfil.

---

## 6. Tecnología

- **React 18** (vía CDN) — componentes y estado.
- **Tailwind CSS** (vía CDN) — estilos utilitarios.
- **Babel Standalone** — JSX en el navegador, sin build.
- 100% estático: se puede abrir como archivo o publicar en GitHub Pages.

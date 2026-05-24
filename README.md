# UniMentor — Plataforma de Mentorías Universitarias

Prototipo de alta fidelidad de una plataforma EdTech que conecta a estudiantes
de primeros semestres con mentores de semestres superiores, al estilo
**Uber matching + chat académico**. El objetivo es facilitar la adaptación
universitaria, reducir la deserción y crear comunidad colaborativa.

Está construido en **un solo archivo `index.html`** (React + Tailwind vía CDN).
No requiere instalar nada ni compilar.

---

## 0. Requisitos previos (qué necesitas de base)

**Solo necesitas dos cosas:**

1. Un **navegador web moderno**: Google Chrome, Microsoft Edge o Firefox
   (cualquiera reciente sirve; viene preinstalado en casi todos los PC).
2. **Conexión a internet** la primera vez que lo abras.

**NO necesitas nada de lo siguiente:**

- ❌ **Python** — no se usa (solo aparece como opción *opcional* en el punto C
  para servir la carpeta; no es obligatorio).
- ❌ **Node.js / npm** — no hay que instalar paquetes.
- ❌ **`npm install` ni descargar librerías** — las librerías que usa
  (React, Tailwind, Babel) **se cargan solas desde internet** mediante CDN
  cuando abres la página. Por eso se necesita internet la primera vez.
- ❌ **Compilar o "buildear"** — el navegador ejecuta todo directamente.
- ❌ Editores, frameworks o configuración previa.

> En resumen: si tienes un navegador e internet, ya puedes ejecutarlo.
> Una vez cargado en el navegador, funciona aunque pierdas la conexión.

---

## 1. Cómo ejecutarlo

No se necesita Node, Python ni programas. Solo un navegador
(Chrome / Edge / Firefox) e internet (la primera vez, para cargar las
librerías y los estilos desde la web).

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
# Lo más simple: abre index.html con doble clic.
# OPCIONAL (no obligatorio): si tienes Python y prefieres un servidor local:
python -m http.server 8000   # luego abre http://localhost:8000
```

### Si no se ve bien

- Necesita internet la primera vez (carga estilos desde la web).
- Si sale en blanco: espera 5–10 segundos y refresca con **F5**.
- Mejor en Chrome o Edge, en pantalla de computador o tablet.

---

## 2. Cómo usar la aplicación

1. En el login, elige un rol: **"Necesito padrino"** (ahijado / estudiante) o
   **"Quiero ser padrino"** (mentor). Los campos vienen con datos de ejemplo.
2. Clic en **Entrar**.
3. Navega con el **menú de la izquierda** (en tablet/móvil, con el botón ☰).

**Recorrido recomendado para una demo completa:**

1. Entra como **ahijado** → *Pedir padrino* → cambia la materia y envía.
2. En **matching** usa el botón **👁 Ver perfil** del padrino → revisa las
   **reseñas estilo Play Store** (resumen 4.9 ★, distribución y comentarios).
3. *Aceptar padrino* → "tocándole la puerta" → **¡Matchaste!** → *Abrir chat*.
4. En el **chat**: manda un mensaje, **adjunta un archivo**, activa
   **compartir pantalla**, prueba el botón **🚩 reportar** (modal de
   Bienestar con categorías), y pulsa **Finalizar** → califica con estrellas.
5. La sesión queda **guardada y resaltada** en *Mis sesiones* — pulsa
   **👁 Ver resumen** para abrir el detalle (temas, recursos, ejercicios,
   notas del padrino).
6. *Cerrar sesión* → entra como **padrino** → acepta/rechaza ahijados,
   revisa logros (con la **beca institucional** resaltada en amarillo) y
   disponibilidad.

---

## 3. Funcionalidades

> Terminología juguetona: el **mentor** se llama **padrino/padrina** y el
> estudiante se llama **ahijado/a**, manteniendo un tono cercano y
> universitario sin perder profesionalismo en formularios y labels.

### Rol Ahijado (busca padrino)
- **Dashboard** con métricas, padrinos recomendados y próxima sesión.
- **Formulario "Pedir padrino"**: materia, tema, descripción, nivel de
  urgencia y horario (con validación).
- **Matching tipo Uber**: búsqueda animada → tarjeta de padrino con foto,
  semestre, especialidad, rating, tiempo de respuesta y estado online →
  *Aceptar / Saltar / Ver perfil* → confirmación del padrino → match.
- **Chat de mentoría**: mensajes en tiempo real, adjuntar archivos,
  compartir pantalla, cronómetro de sesión, panel lateral (temas, recursos,
  ejercicios), botón de **reporte a Bienestar** y modal de **finalizar + valorar**.
- **Perfil completo del padrino**: carrera, semestre, rating, horas,
  logros, historial y **reseñas estilo Play Store** (calificación grande,
  barras de distribución 5★→1★ y comentarios de ahijados anteriores).
- **Mis sesiones**: historial completo con botón **"Ver resumen"** que abre
  un detalle por sesión con temas tratados, recursos utilizados, ejercicios
  asignados y notas del padrino.
- **Mi perfil** con progreso por materia.

### Rol Padrino (estudiante avanzado)
- **Dashboard** con estadísticas, sesión activa y progreso de incentivos
  (con la beca institucional destacada en amarillo).
- **Ahijados en tiempo real**: nombre, materia, urgencia, tiempo desde
  la solicitud, con **Aceptar / Rechazar** funcionales.
- **Mis logros**: horas de servicio social, puntos UniMentor, racha
  diaria, barra de progreso y recompensas desbloqueables (certificados,
  bonos, acceso VIP, **beca institucional**).
- **Disponibilidad**: estado, días, franja horaria y materias que dominas.

### Seguridad y bienestar 🛡️
- **Reportar comportamiento inadecuado** del padrino desde el chat
  o desde su perfil. Modal con cuatro categorías (conducta sexual
  inapropiada · lenguaje verbal ofensivo · acoso psicológico · otro),
  descripción con validación, **reporte anónimo** opcional, ruta directa
  a Bienestar Universitario y línea de emergencias.
- **Padrinos verificados** por la institución (sello dorado en avatares,
  perfil y match).

### Transversal
- Login/Register con selección de rol (ahijado / padrino).
- Notificaciones (toasts) en cada acción.
- Diseño responsive (desktop y tablet) con sidebar colapsable.
- Estética SaaS con paleta institucional: **azul SAP (#0A6ED1)** como
  primario + **amarillo (#F5B82E) institucional** como acento (sellos
  verificados, beca, estrellas, racha, identidad de la universidad).

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
| **Seguridad y bienestar del usuario** | Herramienta de reporte con cuatro categorías (sexual, verbal, psicológico, otro), reporte anónimo, ruta a Bienestar Universitario y línea de emergencias — el prototipo no solo simula la función sino que evidencia compromiso con la protección del estudiante. |
| **Transparencia y confianza (estilo Play Store)** | Perfil del padrino con calificación grande, distribución de estrellas y reseñas de ahijados anteriores, dando contexto real antes de aceptar el match. |
| **Trazabilidad de la sesión** | Cada sesión guarda y permite consultar después un resumen completo: temas tratados, recursos utilizados, ejercicios asignados y notas del padrino — útil para repasar y para auditoría de la institución. |
| **Identidad institucional** | Paleta extendida con **amarillo institucional (#F5B82E)** que aparece en logo, sellos de "padrino verificado", beca institucional y rating, manteniendo el azul SAP como primario. |
| **Tono cercano y comunidad** | Jerga "padrino / ahijado" y copy juvenil ("¡Matchaste!", "Pídele la mano a un padrino") generan pertenencia y bajan la barrera de pedir ayuda — clave para reducir la deserción. |

---

## 5. Pantallas incluidas

Login/Register · Dashboard estudiante · Formulario de solicitud · Matching
mentor-estudiante · Chat de mentoría · Perfil de mentor · Dashboard mentor ·
Solicitudes en tiempo real · Sistema de incentivos · Historial · Disponibilidad
· Configuración de perfil.

---

## 6. Preparado para backend real

El código tiene una **capa `api`** centralizada (ver `API LAYER` en
`index.html`). Hoy devuelve datos mock con latencia simulada; toda la
UI ya es **async-ready**. El día que toque conectar un backend real,
solo se cambia el interruptor `USE_REAL_API = true` y se reemplaza el
cuerpo de cada función — **ningún componente de la UI se modifica**.

Plan paso a paso, tablas y endpoints sugeridos: ver **[`ROADMAP.md`](ROADMAP.md)**.

---

## 7. Tecnología

- **React 18** (vía CDN) — componentes y estado.
- **Tailwind CSS** (vía CDN) — estilos utilitarios.
- **Babel Standalone** — JSX en el navegador, sin build.
- 100% estático: se puede abrir como archivo o publicar en GitHub Pages.

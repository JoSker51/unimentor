# Roadmap — De prototipo a producción

Este documento describe el camino para convertir UniMentor de prototipo
de alta fidelidad a producto real con backend. Está hecho para que el
día que se decida, el trabajo sea **lo más corto y predecible posible**.

---

## Estado actual: ya está semi-listo

El prototipo está construido sobre una **capa `api`** (ver bloque
`API LAYER` dentro de `index.html`). Hoy esa capa devuelve datos mock
con latencia simulada, pero **toda la UI ya es async**. La consecuencia:
el día del backend, **ningún componente de la UI se modifica** — solo
se cambia el cuerpo de las funciones de `api`.

### Lo que ya pasa por la capa `api` (ya async)

| Función                  | Componente que la usa            | Endpoint sugerido              |
|--------------------------|----------------------------------|--------------------------------|
| `api.login`              | `Root` (al iniciar sesión)       | `POST /auth/login`             |
| `api.createRequest`      | `RequestForm` (enviar solicitud) | `POST /requests`               |
| `api.endSession`         | `Chat` (finalizar sesión)        | `POST /sessions`               |
| `api.submitReport`       | `ReportModal` (Bienestar)        | `POST /reports`                |

### Lo que falta pasar por `api` (TODOs marcados en el código)

Existen ya como funciones en la capa, solo falta sustituir la llamada
en su componente (cada uno es 1 línea):

- `api.searchMentors`, `api.getMentorReviews` → `Matching` y `ProfileModal`.
- `api.acceptMentor` → `Matching` (botón "Aceptar padrino").
- `api.mentorAccept` / `api.mentorReject` → `MentorDash` y `MentorRequests`.
- `api.sendMessage`, `api.uploadFile` → `Chat`.
- `api.submitReview` → `EndSessionModal`.
- `api.setAvailability`, `api.updateProfile` → `Availability` y `Settings`.

---

## El día D — pasos para conectar el backend real

### Paso 1 (½ día) · Migrar a Vite

El `babel-standalone` que usa el prototipo no sirve en producción
(es lento y carga el compilador en el navegador). Migrar a Vite es
mecánico:

```bash
npm create vite@latest unimentor-app -- --template react
cd unimentor-app
npm install
npm install tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

Después:

1. Copia todo el bloque `<script type="text/babel">…</script>` de
   `index.html` a `src/App.jsx`.
2. Quita las etiquetas `<script>` y pega la configuración de Tailwind
   en `tailwind.config.js`.
3. Mueve las constantes de mock (`MENTORS`, `REQ0`, etc.) a
   `src/mocks.js` (solo para fallback de desarrollo).
4. Mueve la capa `api` a `src/api.js`.
5. `npm run dev` y listo.

### Paso 2 (½ día) · Elegir stack de backend

**Recomendación: Supabase** — auth + Postgres + realtime + storage en
un solo servicio, sin servidor que mantener. Para un MVP universitario
está sobrado y tiene plan gratuito.

Alternativas según contexto:
- **Firebase**: similar a Supabase, NoSQL.
- **Node + Express + Postgres**: si la institución requiere on-premise.

### Paso 3 (3–5 días) · Implementar tablas y endpoints

```sql
-- Esquema mínimo (Postgres / Supabase)
users          (id, email, password_hash, role, name, career, sem, verified)
requests       (id, ahijado_id, subject, topic, desc, urgency, time, mode, status, created_at)
matches        (id, request_id, mentor_id, chat_id, created_at)
messages       (id, chat_id, sender_id, text, file_url, created_at)
sessions       (id, match_id, dur_minutes, rating, topics, resources, exercises, notes, created_at)
reviews        (id, mentor_id, ahijado_id, rating, comment, created_at)
reports        (id, target_user_id, reporter_id_nullable, category, details, ticket_id, status, created_at)
availability   (mentor_id, days, hour_from, hour_to, subjects)
rewards_progress (mentor_id, hours, points, badges_unlocked)
```

Endpoints — los nombres exactos están en el `API LAYER` de
`index.html`, sección "Mapa función → endpoint".

### Paso 4 (1 día) · Activar el backend en la app

En `src/api.js`:

```js
const USE_REAL_API = true;   // <- el famoso interruptor
const API_BASE = 'https://api.unimentor.edu.co';
```

Si los shapes del backend difieren del mock, se ajustan **dentro de
cada función de `api`** — no se toca ningún componente.

### Paso 5 (2–3 días) · Funcionalidades que requieren backend nuevo

- **WebSockets / Realtime** para chat y matching en vivo
  (Supabase Realtime lo da gratis).
- **Storage** para archivos compartidos en chat.
- **Hashing de contraseñas** y JWT (Supabase Auth lo da hecho).
- **Notificaciones push** (Firebase Cloud Messaging o OneSignal).
- **Job programado** para calcular horas y desbloqueo de recompensas.

---

## Estimación total

| Fase                              | Tiempo       |
|-----------------------------------|--------------|
| 1. Migración a Vite               | ½ día        |
| 2. Setup de Supabase + auth       | 1 día        |
| 3. Tablas y endpoints             | 3–5 días     |
| 4. Conectar la app (flip switch)  | 1 día        |
| 5. Realtime + storage + push      | 2–3 días     |
| **Total realista (1 dev)**        | **8–11 días**|

Con dos personas en paralelo (frontend + backend) cae a ~5–6 días.

---

## Por qué la migración será fácil

1. **La capa `api` ya existe** — solo cambias cuerpos de funciones.
2. **Toda la UI ya es async-ready** — usa `await`, maneja errores con
   toasts y muestra estados de carga (matching tiene "buscando…",
   "esperando confirmación…", spinners).
3. **El esquema de datos está implícito en los mocks** — las constantes
   `MENTORS`, `REQ0`, `SESSIONS0`, `REVIEWS` y `REWARDS` son
   literalmente las filas que tendrá la DB.
4. **Los flujos están probados** — el prototipo simula el camino
   completo, así que sabes qué endpoints necesitas y en qué orden.
5. **La capa `api` tiene latencia simulada** (`sleep(300ms)`), así
   que la UI ya está acostumbrada a esperar respuestas — no aparecerán
   bugs nuevos por timing cuando el backend real responda.

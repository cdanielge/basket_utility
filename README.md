# Basketball Stats

Herramientas web sin dependencias para llevar estadísticas y marcador en partidos de baloncesto. Todo en archivos HTML que se abren directamente en el navegador, sin servidor ni instalación.

## Archivos

| Archivo | Descripción |
|---|---|
| `basketball_stats.html` | Registro de estadísticas por jugador en tiempo real |
| `basketball_scoreboard.html` | Marcador electrónico con cronómetro y chicharra |

---

## basketball_stats.html

### Funcionalidades

- **Box Score** — tabla de jugadores con contadores táctiles para cada estadística
- **Team Stats** — totales del equipo y resumen por jugador
- **Leaders** — top 5 por categoría estadística
- Tema claro / oscuro (persistido en `localStorage`)
- Exportar e importar sesión en JSON
- Los datos se guardan automáticamente en `localStorage` (clave `basketball_stats_v2`)

### Estadísticas registradas

Puntos · Tiros de campo (anotados/intentos) · Triples (anotados/intentos) · Tiros libres (anotados/intentos) · Rebotes · Asistencias · Robos · Bloqueos · Faltas

### Interacción con los contadores

| Acción | Resultado |
|---|---|
| Click en estadística | +1 |
| Doble click en estadística | −1 |
| Click en falta activa | deshace la falta |

### Gestión de jugadores

- Agregar jugador con el botón **+** al pie de la tabla
- Editar nombre y número directamente en la celda
- Eliminar jugador con el ícono de papelera (requiere confirmación; mínimo 1 jugador)

---

## basketball_scoreboard.html

### Funcionalidades

- Marcador para Local y Visitante con nombre editable
- Cronómetro regresivo configurable (por defecto 10 minutos)
- Chicharra al llegar a 00:00 (suena 3 veces)
- Control de período

### Controles

| Acción | Resultado |
|---|---|
| Click en marcador | +1 punto |
| Doble click en marcador | −1 punto |
| Click en cronómetro | iniciar / pausar |
| Doble click en cronómetro | +10 segundos |
| Click en período | +1 período |
| Doble click en período | −1 período |
| Click en **Reset** | reinicia el partido completo |

---

## Uso

1. Abrir el archivo HTML en cualquier navegador moderno.
2. No requiere conexión a internet (las fuentes y los íconos se cargan desde CDN).

## Dependencias externas (CDN)

- [Tabler Icons](https://tabler.io/icons) — íconos en `basketball_stats.html`
- [Barlow / Barlow Condensed](https://fonts.google.com/specimen/Barlow) — tipografía en `basketball_stats.html`
- [Orbitron](https://fonts.google.com/specimen/Orbitron) — tipografía en `basketball_scoreboard.html`

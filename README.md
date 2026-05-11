# 🚀 Práctica de Desarrollo SPEC: EcoRoute

[cite_start]**Módulo:** [cite: 1] Python para administración de sistemas  
[cite_start]**Metodología:** [cite: 5] SPEC-Driven Development (SDD)

---

## 1. Contexto del Proyecto
[cite_start][cite: 4] La empresa de logística **EcoRoute** necesita una herramienta interna para gestionar su nueva flota de furgonetas eléctricas. 

[cite_start][cite: 6] [cite_start]Vuestra labor no es escribir el código directamente, sino actuar como **Arquitectos de Software** y **Product Owners**. [cite: 7] Deberéis redactar la documentación técnica necesaria para que una Inteligencia Artificial (Gemini, Claude, ChatGPT) genere el sistema completo sin errores y bajo vuestras reglas.

---

## 2. El Reto Técnico
[cite_start][cite: 9] Debéis definir un sistema en Python que permita:

[cite_start]* [cite: 10] **Registrar vehículos:** Almacenar ID, modelo y capacidad de batería (0-100%).
* [cite: 11] **Gestionar Entregas:** Cada entrega tiene una ubicación y un consumo estimado de batería.
[cite_start]* [cite: 12] **Lógica de Seguridad (Crítico):** Si una ruta consume más del 80% de la batería actual, el sistema debe rechazar la ruta o sugerir una parada en un punto de recarga.

### 📋 Modelo de Datos Requerido

| Entidad | Atributos |
| :--- | :--- |
| [cite_start]**Vehículo (`Vehicle`)** [cite: 14] | [cite_start]`id_vehiculo` (alfanumérico) [cite: 15], `modelo` [cite: 16], `capacidad_bateria_total` (kWh) [cite: 17], `nivel_bateria_actual` (%) [cite: 18], `autonomia_maxima_km` [cite: 19], `estado` (Enum: Disponible, En Ruta, Cargando, Mantenimiento)[cite: 20]. |
| [cite_start]**Entrega (`Delivery`)** [cite: 21] | [cite_start]`id_entrega` [cite: 22][cite_start], `destino_coordenadas` (lat, lon) [cite: 23][cite_start], `peso_kg` [cite: 24][cite_start], `prioridad` (1-3) [cite: 25][cite_start], `ventana_horaria`[cite: 26]. |
| [cite_start]**Ruta (`Route`)** [cite: 27] | [cite_start]`id_ruta` [cite: 28][cite_start], `vehiculo_asignado` (FK) [cite: 29][cite_start], `lista_entregas` [cite: 30][cite_start], `distancia_total_estimada` [cite: 31][cite_start], `consumo_estimado_bateria`[cite: 32]. |

---

## 3. Entrega y Estructura
[cite_start][cite: 34] [cite_start]Deberéis crear una carpeta en vuestro GitHub llamada `/ecoroute` con los siguientes archivos Markdown. [cite: 63] Todos los ficheros deben tener control de versiones, tablas y un formato profesional.

### 📂 Ficheros de Especificación
* [cite_start]**`architecture.md` (La Estructura):** [cite: 37] [cite_start]Organización del código (Arquitectura Limpia) y persistencia (JSON o SQLite)[cite: 38].
* [cite_start]**`spec.md` (Los Requisitos):** [cite: 41] Funciones principales, parámetros de entrada y lógica matemática de autonomía.
* [cite_start]**`agents.md` (Los Roles de la IA):** [cite: 44] Instrucciones para agentes "Senior Developer", "QA Tester" y "Documentador".
* [cite_start]**`decisions.md` (El Histórico):** [cite: 47] Justificación de Python 3.10+, manejo de errores y elección de librerías.
* [cite_start]**`constitution.md` (Las Reglas):** [cite: 56] [cite_start]Idioma (código en inglés, comentarios en español) y normas de nomenclatura (`snake_case`, `PascalCase`, `UPPER_CASE`)[cite: 57].

### [cite_start]📦 Librerías Obligatorias [cite: 48]
[cite_start]* [cite: 49] **Validación:** `Pydantic`
* [cite: 50] **Interfaz:** `Rich`
[cite_start]* [cite: 51] **Persistencia:** `TinyDB` o `Sqlite3`
[cite_start]* [cite: 52] **Geolocalización:** `Geopy`
* [cite: 53] **Configuración:** `python-dotenv`

---

## 4. Flujo de Trabajo
[cite_start]1. [cite: 65] **Redacción:** Escribid los 5 ficheros asegurándoos de que no haya contradicciones.
[cite_start]2. [cite: 66] **Prompting:** Subid los archivos a Gemini con el comando: 
   > [cite_start]*"Analiza estos 5 ficheros de especificación. Siguiendo estrictamente sus directrices, genera el código Python necesario para el sistema EcoRoute. Asegúrate de que los agentes definidos en agents.md cumplan su función y que se respete la constitution.md."* [cite: 67]
[cite_start]3. [cite: 68] [cite_start]**Validación:** Si hay errores, **no corrijáis el código a mano**. [cite: 69] Corregid el fichero SPEC correspondiente y pedid a la IA que genere la solución de nuevo.

---

## [cite_start]5. Rúbrica de Evaluación [cite: 70]
| Criterio | Excelente (5 pts) | Insuficiente (0 pts) |
| :--- | :--- | :--- |
| [cite_start]**Especificación (spec.md)** [cite: 76] | [cite_start]Precisión total en lógica y tipos[cite: 77]. | [cite_start]Requisitos vagos o inexistentes[cite: 80]. |
| [cite_start]**Arquitectura** [cite: 81] | [cite_start]Uso de librerías y estructura modular[cite: 82]. | [cite_start]Sin estructura ni justificación[cite: 85]. |
| [cite_start]**Constitución** [cite: 86] | [cite_start]Respeta `snake_case` y *Type Hints*[cite: 87]. | [cite_start]Estilo inconsistente[cite: 90]. |
| [cite_start]**Gestión de Agentes** [cite: 91] | [cite_start]Roles activos que mejoran el código[cite: 92]. | [cite_start]No utiliza el concepto de agentes[cite: 95]. |
| [cite_start]**Funcionalidad** [cite: 96] | [cite_start]Pasa tests y cumple lógica de batería[cite: 97]. | [cite_start]El código no ejecuta[cite: 100]. |

---
[cite_start]**Entrega:** [cite: 62] Compartir el proyecto con **mnarrieta@iesfuengirola1.es**.

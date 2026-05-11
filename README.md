# Python para administración de sistemas
## Práctica de desarrollo SPEC

### 1. Contexto del Proyecto
[cite_start]La empresa de logística EcoRoute necesita una herramienta interna para gestionar su nueva flota de furgonetas eléctricas[cite: 4]. [cite_start]A diferencia de un desarrollo tradicional, utilizaremos SPEC-Driven Development (SDD)[cite: 5].

[cite_start]Vuestra labor no es escribir el código directamente, sino actuar como Arquitectos de Software y Product Owners[cite: 6]. [cite_start]Deberéis redactar la documentación técnica necesaria para que una Inteligencia Artificial (Gemini, Claude, ChatGPT) genere el sistema completo sin errores y bajo vuestras reglas[cite: 7].

---

### 2. El Reto Técnico
[cite_start]Debéis definir un sistema en Python que permita[cite: 9]:
* [cite_start]**Registrar vehículos**: Almacenar ID, modelo y capacidad de batería (0-100%)[cite: 10].
* [cite_start]**Gestionar Entregas**: Cada entrega tiene una ubicación y un consumo estimado de batería[cite: 11].
* [cite_start]**Lógica de Seguridad (Crítico)**: Si una ruta consume más del 80% de la batería actual, el sistema debe rechazar la ruta o sugerir una parada en un punto de recarga[cite: 12].

#### Modelo de datos:

**Entidad: Vehículo (Vehicle)**
* **id_vehiculo (String)**: Identificador único (ej: "VAN-001"). [cite_start]Debe seguir un patrón alfanumérico[cite: 15].
* [cite_start]**modelo (String)**: Nombre del modelo (ej: "Tesla Semi", "Renault Kangoo ZE")[cite: 16].
* **capacidad_bateria_total (Float)**: Capacidad máxima en kWh[cite: 17].
* [cite_start]**nivel_bateria_actual (Int/Float)**: Porcentaje de carga actual (0 a 100)[cite: 18].
* [cite_start]**autonomia_maxima_km (Int)**: Cuántos km puede recorrer con el 100% de carga[cite: 19].
* **estado (Enum)**: Disponible, En Ruta, Cargando, Mantenimiento[cite: 20].

**Entidad: Entrega / Pedido (Delivery)**
* [cite_start]**id_entrega (String)**: Identificador único del paquete[cite: 22].
* **destino_coordenadas (Tuple: lat, lon)**: Ubicación exacta de la entrega[cite: 23].
* **peso_kg (Float)**: Influye en el consumo (opcional para aumentar dificultad)[cite: 24].
* **prioridad (Int)**: Nivel de urgencia (1-3)[cite: 25].
* [cite_start]**ventana_horaria (String)**: Ejemplo: "09:00 – 11:00"[cite: 26].

**Entidad: Ruta (Route)**
* **id_ruta (String)**: ID de la jornada[cite: 28].
* **vehiculo_asignado (FK)**: Referencia al ID del vehículo[cite: 29].
* **lista_entregas (List)**: Lista ordenada de IDs de entregas[cite: 30].
* **distancia_total_estimada (Float)**: Suma de los trayectos en km[cite: 31].
* [cite_start]**consumo_estimado_bateria (Float)**: Porcentaje que se restará tras completar la ruta[cite: 32].

---

### 3. Entrega
[cite_start]Deberéis crear una carpeta en tu espacio github llamada `/ecoroute` con los siguientes archivos Markdown[cite: 34]. [cite_start]Cada uno tiene un propósito estricto[cite: 35]:

| Archivo | Propósito | Contenido Requerido |
| :--- | :--- | :--- |
| **architecture.md** | La Estructura | Organización del código. [cite_start]Arquitectura limpia y persistencia (JSON o SQLite)[cite: 36, 37, 38]. |
| **spec.md** | Los Requisitos | Qué hace el programa. [cite_start]Funciones, parámetros, tipos y cálculos de autonomía[cite: 39, 40, 41]. |
| **agents.md** | Los Roles de la IA | Cómo debe "pensar" la IA. [cite_start]Instrucciones para Senior Developer, QA Tester y Documentador[cite: 42, 43, 44]. |
| **decisions.md** | Histórico de Decisiones | Justificación técnica. [cite_start]Python 3.10+, librerías específicas y manejo de errores[cite: 45, 46, 47]. |
| **constitution.md** | Las Reglas de Oro | Restricciones éticas y de formato. [cite_start]Idioma (Código: Inglés / Comentarios: Español)[cite: 54, 55, 56]. [cite_start]Nomenclatura: snake_case, PascalCase y SCREAMING_SNAKE_CASE[cite: 57]. |

#### Librerías necesarias:
* **Validación de Datos**: Pydantic[cite: 49].
* [cite_start]**Interfaz de Usuario**: Rich[cite: 50].
* [cite_start]**Persistencia**: TinyDB o Sqlite3[cite: 51].
* **Cálculos Geográficos**: Geopy[cite: 52].
* [cite_start]**Configuración**: python-dotenv[cite: 53].

---

### 4. Flujo de Trabajo
1. [cite_start]**Redacción**: Escribid los 5 ficheros sin contradicciones[cite: 65].
2. [cite_start]**Prompting**: Subid los ficheros con el comando: *"Analiza estos 5 ficheros de especificación... genera el código Python necesario..."*[cite: 66, 67].
3. **Validación**: Ejecutad el código. [cite_start]Si hay errores, corregid el fichero SPEC, no el código a mano[cite: 68, 69].

---

### 5. Rúbrica de Evaluación
* **Calidad de la Especificación**: Precisión en endpoints, batería y tipos[cite: 76, 77].
* [cite_start]**Arquitectura y Decisiones**: Justificación de librerías y estructura modular[cite: 81, 82].
* [cite_start]**Cumplimiento de la Constitución**: Estilo de código, nomenclatura y Type Hints[cite: 86, 87].
* **Gestión de Agentes**: Roles específicos que mejoren la calidad[cite: 91, 92].
* [cite_start]**Funcionalidad y Validación**: Lógica del 20% de batería y tests unitarios correctos[cite: 96, 97].

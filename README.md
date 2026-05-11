Práctica de Desarrollo: Sistema de Gestión "EcoRoute" con Metodología SPEC
1. Contexto del Proyecto
La empresa de logística EcoRoute necesita una herramienta interna para gestionar su nueva flota de furgonetas eléctricas. A diferencia de un desarrollo tradicional, utilizaremos SPEC-Driven Development (SDD).
Vuestra labor no es escribir el código directamente, sino actuar como Arquitectos de Software y Product Owners. Deberéis redactar la documentación técnica necesaria para que una Inteligencia Artificial (Gemini, Claude, ChatGPT) genere el sistema completo sin errores y bajo vuestras reglas.

2. El Reto Técnico
Debéis definir un sistema en Python que permita:
    1. Registrar vehículos: Almacenar ID, modelo y capacidad de batería (0-100%).
    2. Gestionar Entregas: Cada entrega tiene una ubicación y un consumo estimado de batería.
    3. Lógica de Seguridad (Crítico): Si una ruta consume más del 80% de la batería actual, el sistema debe rechazar la ruta o sugerir una parada en un punto de recarga.
    4. Modelo de datos:
        ◦ Entidad: Vehículo (Vehicle): Representa cada unidad de la flota. Es el objeto principal que consume recursos.
            ▪ id_vehiculo (String): Identificador único (ej: "VAN-001"). Debe seguir un patrón alfanumérico.
            ▪ modelo (String): Nombre del modelo (ej: "Tesla Semi", "Renault Kangoo ZE").
            ▪ capacidad_bateria_total (Float): Capacidad máxima en kWh.
            ▪ nivel_bateria_actual (Int/Float): Porcentaje de carga actual (0 a 100).
            ▪ autonomia_maxima_km (Int): Cuántos km puede recorrer con el 100% de carga.
            ▪ estado (Enum): Disponible, En Ruta, Cargando, Mantenimiento.
        ◦ Entidad: Entrega / Pedido (Delivery): Representa el trabajo que debe realizar el vehículo.
        ◦ id_entrega (String): Identificador único del paquete.
        ◦ destino_coordenadas (Tuple: lat, lon): Ubicación exacta de la entrega.
        ◦ peso_kg (Float): Influye en el consumo (opcional para aumentar dificultad).
        ◦ prioridad (Int): Nivel de urgencia (1-3).
        ◦ ventana_horaria (String): Ejemplo: "09:00 – 11:00".
    • Entidad: Ruta (Route): Es la entidad lógica que vincula un Vehículo con varias Entregas.
        ◦ id_ruta (String): ID de la jornada.
        ◦ vehiculo_asignado (FK): Referencia al ID del vehículo.
        ◦ lista_entregas (List): Lista ordenada de IDs de entregas.
        ◦ distancia_total_estimada (Float): Suma de los trayectos en km.
        ◦ consumo_estimado_bateria (Float): Porcentaje que se restará tras completar la ruta.
           

3. Entrega 
Deberéis crear una carpeta en tu espacio github llamada /ecoroute con los siguientes archivos Markdown. Cada uno tiene un propósito estricto:
    • architecture.md (La Estructura)
        ◦ Define cómo se organiza el código.
        ◦ Debe incluir: El uso de una arquitectura limpia (separación entre lógica de negocio y entrada de datos) y qué persistencia usar (ej. ficheros JSON o SQLite).
    • spec.md (Los Requisitos)
        ◦ Define qué hace el programa.
        ◦ Debe incluir: Descripción de las funciones principales, parámetros de entrada, tipos de datos y los cálculos matemáticos para la autonomía.
    • agents.md (Los Roles de la IA)
        ◦ Define cómo debe "pensar" la IA al leer tus archivos.
        ◦ Debe incluir: Instrucciones para un agente "Senior Developer" (código limpio), un agente "QA Tester" (que cree pruebas unitarias) y un agente "Documentador".
    • decisions.md (El Histórico de Decisiones)
        ◦ Justifica tus elecciones técnicas.
        ◦ Debe incluir: Por qué usas Python 3.10+, por qué eliges una librería específica (ej. Rich para la interfaz de consola o Pydantic para validar datos) y cómo manejas los errores.
        ◦ Librerías necesarias:
            ▪ Validación de Datos: Pydantic
            ▪ Interfaz de Usuario (Consola): Rich
            ▪ Persistencia de Datos: TinyDB o Sqlite3
            ▪ Cálculos Geográficos: Geopy
            ▪ Entorno y Configuración: python-dotenv
    • constitution.md (Las Reglas de Oro)
        ◦ Define las restricciones éticas y de formato.
        ◦ Debe incluir: Idioma del código (inglés) vs idioma de comentarios (español).
        ◦ Nomenclatura: Se usará snake_case para variables, funciones y métodos; PascalCase para clases; y SCREAMING_SNAKE_CASE para constantes globales.
    • proyecto_ecoroute.zip
        ◦ Con la estructura de la carpeta /ecoroute con todos los ficheros comprimidos en sus respectivas carpetas generados por la IA.
    • readme.md
        ◦ Con la descripción del proyecto

    • Compartir el proyecto (en privado) con el usuario mnarrieta (mnarrieta@iesfuengirola1.es)
    • Todos los ficheros .md deben tener control de versiones, tablas y un correcto formato cumpliendo los estándares Markdown.

4. Flujo de Trabajo
    1. Redacción: Escribid los 5 ficheros asegurándoos de que no haya contradicciones (ej. no pidas SQLite en architecture y JSON en decisions).
    2. Prompting: Subid los 5 archivos a Gemini con el siguiente comando, por ejemplo:
       "Analiza estos 5 ficheros de especificación. Siguiendo estrictamente sus directrices, genera el código Python necesario para el sistema EcoRoute. Asegúrate de que los agentes definidos en agents.md cumplan su función y que se respete la constitution.md."
    3. Validación: Ejecutad el código resultante. Si la IA comete un error, no corrijáis el código a mano. Debéis corregir el fichero SPEC correspondiente y volver a pedirle a la IA que genere la solución.

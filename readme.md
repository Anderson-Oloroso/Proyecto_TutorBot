# TutorBot: Sistema Automatizado de Gestión de Tutorías Académicas 🤖🎓

[![n8n](https://img.shields.io/badge/Automation-n8n-FF6C37?style=for-the-badge&logo=n8n&logoColor=white)](https://n8n.io/)
[![Telegram](https://img.shields.io/badge/Bot-Telegram-26A5E4?style=for-the-badge&logo=telegram&logoColor=white)](https://telegram.org/)
[![Google Sheets](https://img.shields.io/badge/Database-Google%20Sheets-34A853?style=for-the-badge&logo=google-sheets&logoColor=white)](https://docs.google.com/spreadsheets/)

## 📝 1. Introducción
En el entorno educativo actual, la coordinación de asesorías académicas suele ser un proceso caótico y manual. Los estudiantes dependen de correos electrónicos o mensajes informales para encontrar un tutor, mientras que los tutores no tienen una agenda centralizada para gestionar su disponibilidad. Este proceso genera cruces de horarios, desatención de materias críticas y falta de trazabilidad.

**TutorBot** es una solución automatizada desarrollada en **n8n** que conecta a estudiantes con tutores mediante un motor de asignación inteligente. El sistema gestiona desde la solicitud inicial hasta la finalización de la asesoría, garantizando que cada materia cuente con el tutor adecuado en el horario disponible, optimizando así el recurso humano y mejorando el rendimiento académico.

---

## 🎯 2. Objetivos del Proyecto
* **Desarrollar un sistema automatizado** para la gestión de tutorías académicas que integre Telegram, Google Sheets y lógica avanzada de asignación.
* **Implementar un motor de búsqueda** que asocie automáticamente materia, tutor y horario libre.
* **Diseñar una interfaz conversacional** en Telegram para la autogestión del estudiante (Solicitar, consultar, cancelar).
* **Automatizar el control de estados** de la tutoría (*Solicitada, Asignada, Confirmada, Finalizada*).
* **Validar disponibilidad en tiempo real** para evitar cruces de agenda o doble reserva.
* **Generar reportes automáticos** de actividad para la coordinación académica.

---

## ⚙️ 3. Descripción del Sistema & Arquitectura

El sistema está compuesto por tres módulos principales interconectados de forma síncrona:
### 🔹 A. Interfaz en Telegram
Es el punto de contacto único y amigable para el estudiante, el cual le permite:
* Registrarse como estudiante en la plataforma.
* Seleccionar materias académicas mediante menús numéricos interactivos.
* Consultar en tiempo real el estado actual de sus solicitudes.
* Recibir recordatorios y alertas automáticas de sus citas programadas.

### 🔹 B. Motor de Automatización (n8n)
Es el núcleo central u orquestador encargado de procesar toda la lógica de negocio:
1.  **Gestión de Sesiones (State Machine):** Mantiene el estado activo del usuario para guiarlo a través de flujos de varios pasos (Mecanismo Wizard).
2.  **Lógica de Asignación Inteligente:** Realiza consultas cruzadas en la base de datos para emparejar tutores activos que dicten la materia y tengan franjas horarias libres.
3.  **Sistema de Notificaciones:** Despacha alertas asíncronas inmediatas al estudiante y al tutor asignado en cuanto ocurre un emparejamiento exitoso.

### 🔹 C. Modelo de Datos (Google Sheets)
Estructura relacional de la base de datos denominada `TutorBot_DB`, dividida en las siguientes hojas de cálculo:

#### 📊 Hoja: `TUTORES`
| Campo | Tipo | Descripción |
| :--- | :--- | :--- |
| `id_tutor` | Alfanumérico | Identificador único del tutor |
| `nombre` | Texto | Nombre completo del docente/tutor |
| `especialidad_materias` | Texto (CSV) | Materias que está capacitado para impartir |
| `estado` | Texto | Estado operativo (`Activo` / `Inactivo`) |

#### 📅 Hoja: `DISPONIBILIDAD`
| Campo | Tipo | Descripción |
| :--- | :--- | :--- |
| `id_dispo` | Alfanumérico | Identificador único de la franja horaria |
| `id_tutor` | Alfanumérico | Relación con la hoja de TUTORES |
| `dia_semana` | Texto | Día asignado (Ej: Lunes, Martes) |
| `hora_inicio` | Tiempo (HH:MM) | Hora de inicio de la disponibilidad |
| `hora_fin` | Tiempo (HH:MM) | Hora de finalización de la disponibilidad |
| `estado` | Texto | Disponibilidad actual (`Libre` / `Ocupado`) |

#### 🎓 Hoja: `TUTORIAS`
| Campo | Tipo | Descripción |
| :--- | :--- | :--- |
| `id_tutoria` | Alfanumérico | Código único de control de tutoría |
| `id_estudiante` | Alfanumérico | ID de Telegram o registro del alumno |
| `id_tutor` | Alfanumérico | ID del tutor asignado |
| `materia` | Texto | Asignatura de la tutoría |
| `fecha` | Fecha (YYYY-MM-DD) | Fecha de ejecución de la sesión |
| `hora` | Tiempo (HH:MM) | Horario pactado |
| `estado` | Texto | Estado del flujo (`Solicitada`, `Asignada`, `Confirmada`, `Finalizada`) |

#### 🔄 Hoja: `SESSIONS`
| Campo | Tipo | Descripción |
| :--- | :--- | :--- |
| `telegram_user` | Numérico (ID) | Chat ID único de Telegram del usuario |
| `pantalla_actual` | Texto | Vista o menú donde se encuentra el usuario |
| `paso_actual` | Numérico | Paso secuencial dentro del Wizard activo |
| `datos_parciales` | JSON / Texto | Payload temporal guardado durante el flujo de reserva |

---

## 🔄 4. Flujo Guiado del Estudiante (Wizard)

El flujo principal de **"Solicitar Tutoría"** opera de manera secuencial para evitar errores de entrada:

---

## 📈 5. Resultados Esperados
* ⚡ **Reducción del 90%** en el tiempo operativo de asignación y emparejamiento de tutorías.
* 🔍 **Trazabilidad Total:** Registro e historial auditor completo (quién solicitó, quién atendió, fechas y horas de cierre).
* 🚀 **Escalabilidad Alta:** Capacidad arquitectónica para gestionar cientos de tutores y estudiantes concurrentes.
* 💎 **Experiencia de Usuario Integrada:** Interfaz conversacional fluida que guía al estudiante paso a paso eliminando la fricción de manuales de usuario.

---

## 📦 6. Componentes de la Entrega & Despliegue

### 👥 Datos del Grupo de Trabajo
* **Nombre del Repositorio:** `Proyecto_TutorBot_ApellidoNombre`
* **Integrantes:** *[Completar con los integrantes asignados por el Trainer]*

### 📁 Archivos Incluidos en este Repositorio:
1.  `README.md`: Este archivo guía con las especificaciones generales del proyecto.
2.  `TutorBot_Workflow.json`: Archivo comprimido/exportado con el flujo completo construido en n8n listo para importar.
3.  `Capturas/`: Carpeta que almacena los screenshots evidenciando el flujo correcto del Bot en Telegram y los nodos de n8n.

### 🔗 Accesos Compartidos externos:
* [Enlace al Google Sheets de la Base de Datos (TutorBot_DB)](#) *(Asegurar de dar permisos de edición para los evaluadores)*
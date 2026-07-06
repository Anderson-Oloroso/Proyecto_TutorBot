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
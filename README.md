# VetClinic App

Aplicación móvil para una clínica veterinaria construida con **Flutter + Firebase**. Incluye autenticación (email/Google), gestión de citas, historias clínicas, notificaciones push (FCM), roles (Cliente/Doctor/Admin) y pagos (sandbox).

## 🎯 Objetivo
Ampliar mi portafolio como ingeniero de sistemas con una app funcional, escalable y bien documentada.

## 🚀 Alcance (v1)
- Autenticación segura (Email/Google), verificación y recuperación de contraseña.
- Pantalla institucional (misión, visión, servicios, perfiles).
- Citas: crear, listar, editar/cancelar; vistas por cliente y doctor.
- Historias clínicas: CRUD por mascota (edición solo por doctor).
- Notificaciones de recordatorio (FCM).
- Roles y permisos (Cliente, Doctor, Admin).
- Pagos en sandbox (PayPal/PayU) y registro de transacciones.

## 🧰 Stack
- **Frontend móvil:** Flutter (Dart)
- **BaaS:** Firebase (Auth, Firestore, Storage, FCM)
- **CI/CD:** GitHub Actions (más adelante)
- **Docs:** `/docs` (requerimientos, arquitectura, data model, wireframes)

## 🗺️ Roadmap por fases
1) Diseño y planificación  
2) Configuración del entorno  
3) Autenticación  
4) Módulo institucional  
5) Gestión de citas  
6) Historia clínica  
7) Notificaciones  
8) Roles y permisos  
9) Pagos  
10) Pruebas y despliegue

## 📂 Estructura (inicial)

vetclinic-app/
├─ docs/
├─ README.md
├─ LICENSE
└─ .gitignore

## 👨🏻‍💻 Cómo ejecutar (pronto)
Se documentará en `/docs/setup.md` cuando se cree el proyecto Flutter en `/app`.
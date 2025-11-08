# Requerimientos del Proyecto — VetClinic App

## 1) Objetivos SMART
1. **Publicar** una versión en **Closed Testing (Google Play Console)** en **≤ 14 semanas**, trabajando 3h/día (L–V).
2. Completar **100%** de flujos críticos en v1: registro/login, crear cita, editar historia (doctor), recibir recordatorio, pago sandbox.
3. Alcanzar **≥ 90%** de casos de prueba manuales verdes y **≥ 60%** de cobertura en servicios/core.
4. Mantener **tiempo de respuesta < 300 ms** en operaciones comunes (login, listar citas) con conexión estable.
5. Documentar cada fase con capturas/GIFs y publicar un **video demo** final en el README.

## 2) Alcance (v1)
- Autenticación (Email/Google), verificación de email y recuperación de contraseña.
- Pantalla institucional: misión, visión, servicios, perfiles de doctoras.
- Citas: crear/editar/cancelar; vistas por cliente y por doctor; estado (pendiente, confirmada, cancelada).
- Historias clínicas: CRUD por mascota; **solo el doctor edita**; adjuntos (imágenes/PDF).
- Notificaciones push (FCM) para recordatorios T-24h y T-2h.
- Roles y permisos: **Cliente**, **Doctor**, **Administrador**.
- Pagos (sandbox PayPal o PayU) y registro de transacciones.
- **Fuera de alcance v1:** chat en tiempo real, iOS release, multimoneda avanzada.

## 3) Actores y Roles
- **Cliente (Dueño):** registro/login; gestiona mascotas; agenda/gestiona sus citas; ve historias propias (solo lectura); realiza pagos.
- **Doctor:** ve su agenda; confirma/reagenda/cancela citas propias; crea/edita historias.
- **Administrador:** gestiona contenidos institucionales y usuarios; acceso total de lectura.

## 4) Casos de Uso (resumen)
- **UC-01** Registrarse (Cliente)
- **UC-02** Iniciar sesión (Cliente/Doctor/Admin)
- **UC-03** Recuperar contraseña
- **UC-04** Verificar email
- **UC-05** Gestionar perfil mínimo (nombre/rol)
- **UC-06** Crear/Editar/Cancelar cita (Cliente)
- **UC-07** Ver citas del doctor (Doctor)
- **UC-08** Confirmar/Reagendar/Cancelar cita (Doctor)
- **UC-09** CRUD historia clínica (Doctor)
- **UC-10** Ver historia propia (Cliente)
- **UC-11** Notificaciones de recordatorio (FCM)
- **UC-12** Pago sandbox + comprobante
- **UC-13** Gestión institucional (Admin)

## 5) Criterios de Aceptación (Gherkin)

### Autenticación
```gherkin
Feature: Autenticación con correo
  Scenario: Registro exitoso
    Given que estoy en la pantalla de registro
    When ingreso email válido y contraseña fuerte
    And acepto términos
    Then se crea la cuenta
    And recibo un email de verificación

  Scenario: Inicio con email no verificado
    Given que tengo una cuenta sin verificar
    When inicio sesión
    Then veo un aviso para verificar
    And no puedo crear citas hasta verificar

    Feature: Gestión de citas
  Scenario: Cliente crea una cita válida
    Given que soy Cliente autenticado y tengo una mascota registrada
    When selecciono doctora, fecha y hora disponibles
    Then la cita se guarda con estado "pendiente"
    And veo confirmación visual

  Scenario: Doctor confirma una cita
    Given que soy Doctor autenticado y tengo citas pendientes
    When confirmo una cita
    Then el estado cambia a "confirmada"
    And el Cliente recibe notificación

Feature: Historias clínicas
  Scenario: Doctor crea historia clínica
    Given que soy Doctor autenticado
    When registro motivo, diagnóstico y tratamiento para una mascota
    Then se guarda la historia con referencia a la mascota y al doctor

  Scenario: Cliente ve historia de su mascota
    Given que soy Cliente autenticado
    When abro el detalle de mi mascota
    Then puedo ver la historia clínica en solo lectura

6) Requerimientos No Funcionales (NFR)

Seguridad: reglas de Firestore por rol; verificación de email obligatoria; almacenamiento seguro de tokens FCM.

Rendimiento: listas paginadas; consultas indexadas.

Escalabilidad: arquitectura modular (Clean + Riverpod/Bloc); BaaS Firebase; colas de notificaciones.

Accesibilidad: tamaños/contrastes correctos; navegación por teclado; labels en inputs.

Mantenibilidad: linters; pre-commit; CI básica; ADRs para decisiones técnicas.

Costo: plan gratuito de Firebase; evitar operaciones costosas.

7) Suposiciones y Riesgos

Dispositivos Android 8+.

Conectividad a Internet requerida para funciones en línea.

Riesgo: tiempos de aprobación de pasarela/políticas de Play Store.



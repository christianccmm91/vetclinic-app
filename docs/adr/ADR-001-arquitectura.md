# ADR-001 — Arquitectura base: Flutter + Firebase

- **Fecha:** YYYY-MM-DD
- **Estado:** accepted
- **Contexto:** Se requiere construir una app móvil completa para una clínica veterinaria como parte de un portafolio profesional. Debe ser funcional, escalable, con autenticación, base de datos, notificaciones, roles y pagos, utilizando tecnologías modernas y gratuitas en lo posible.

## Decisión
Adoptar **Flutter** (Dart) para el frontend móvil y **Firebase** como BaaS (Auth, Firestore, Storage, Cloud Messaging).

## Consecuencias
**Pros**
- Desarrollo rápido con un único código para Android/iOS.
- UI consistente y de alto rendimiento (render propio de Flutter).
- Integración directa con Firebase: Auth, Firestore, FCM y Storage.
- Amplio ecosistema, buen material educativo, plan gratuito viable para v1.

**Contras**
- Aprendizaje inicial de Dart/Flutter si no se conoce.
- Dependencia de servicios Firebase (vendor lock-in parcial).
- Para iOS se requiere macOS/Apple para compilar y publicar.

## Alternativas consideradas
1. **React Native + Supabase**
   - Pros: JavaScript conocido, Supabase open-source, Postgres.
   - Contras: mayor complejidad de integración push/roles; rendimiento UI variable según librerías.

2. **Ionic (Capacitor) + Firebase**
   - Pros: HTML/CSS/JS conocidos, rapidez para prototipos.
   - Contras: WebView; rendimiento inferior; más trabajo para UX nativa.

## Impacto en seguridad y costos
- Reglas de seguridad de Firestore por rol (Cliente/Doctor/Admin).
- Verificación obligatoria de email y control de acceso por claims.
- Uso de plan gratuito de Firebase para v1 (vigilar límites).

## Métricas de éxito
- Flujos críticos funcionando (login, citas, historias, notificaciones, pagos sandbox).
- Rendimiento aceptable (<300 ms en operaciones comunes).
- Documentación y CI básica funcionando.

## Estado futuro
- Evaluar en v2: backend propio (NestJS) o Supabase si se requiere SQL/relaciones complejas.

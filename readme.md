# Sistema de salud para pacientes

Plataforma web y móvil que permite a los pacientes gestionar su atención médica: agendar citas, consultar su historia clínica, hacer seguimiento a medicamentos y órdenes, comunicarse con el personal de salud y pagar copagos en línea. Incluye perfiles para médicos y para personal administrativo.

> **Estado del proyecto:** fase de definición de requerimientos e historias de usuario.

## equipo de trabajo

- Product Owner: Norma Isbelia Gil Suarez
- sprint master: Sergio Esteban Lozano Yepes
- desarrollador: Laura Camila Tabares Arroyabe

## Contenido

- [Objetivo](#objetivo)
- [Roles de usuario](#roles-de-usuario)
- [Módulos y requerimientos funcionales](#módulos-y-requerimientos-funcionales)
- [Historias de usuario](#historias-de-usuario)
- [Alcance sugerido del MVP](#alcance-sugerido-del-mvp)
- [Requisitos transversales](#requisitos-transversales)
- [Estructura del repositorio](#estructura-del-repositorio)
- [Próximos pasos](#próximos-pasos)

---

## Objetivo

Facilitar el acceso de los pacientes a los servicios de salud, reducir los trámites presenciales y mejorar la comunicación entre pacientes, médicos y la entidad, garantizando la seguridad y la privacidad de la información clínica.

## Roles de usuario

| Rol | Descripción |
|---|---|
| **Paciente** | Usuario principal. Gestiona sus citas, consulta su historia clínica y se comunica con el personal de salud. |
| **Titular / cuidador** | Paciente que además administra a sus dependientes (hijos, adultos mayores). |
| **Médico** | Configura su agenda, registra consultas, diagnósticos, fórmulas y órdenes. |
| **Administrador** | Gestiona usuarios, roles, especialidades y sedes, y consulta reportes. |

## Módulos y requerimientos funcionales

| # | Módulo | Requerimientos | Resumen |
|---|---|---|---|
| 1 | Registro y autenticación | RF-01 a RF-06 | Registro, inicio de sesión, recuperación de contraseña, verificación en dos pasos, edición de perfil y grupo familiar. |
| 2 | Gestión de citas médicas | RF-07 a RF-15 | Consulta de especialidades y agenda, solicitud, reprogramación y cancelación, confirmaciones, recordatorios, historial, lista de espera y telemedicina. |
| 3 | Historia clínica | RF-16 a RF-23 | Consulta de solo lectura de diagnósticos, evoluciones, resultados, fórmulas y órdenes; descarga en PDF y registro de accesos. |
| 4 | Medicamentos y órdenes | RF-24 a RF-26 | Seguimiento de fórmulas vigentes, recordatorios de toma y solicitud de autorizaciones. |
| 5 | Notificaciones y comunicación | RF-27 a RF-30 | Centro de notificaciones, preferencias por canal, mensajería segura y PQRS. |
| 6 | Pagos y facturación | RF-31 a RF-33 | Copagos y cuotas moderadoras, pago en línea y descarga de facturas. |
| 7 | Médico y administración | RF-34 a RF-38 | Agenda del médico, registro de consulta, acceso a historias, gestión administrativa y reportes. |

## Historias de usuario

Las 38 historias de usuario (una por requerimiento, con criterios de aceptación y prioridad) están en:

📄 [`historias_de_usuario_sistema_salud.md`](./historias_de_usuario_sistema_salud.md)

Formato utilizado: **Como** [rol], **quiero** [acción], **para** [beneficio].

## Alcance sugerido del MVP

Historias con prioridad alta que permiten un primer flujo completo de atención:

- **Acceso:** HU-01, HU-02, HU-03.
- **Citas:** HU-07, HU-08, HU-09, HU-10, HU-11, HU-12, HU-15.
- **Historia clínica:** HU-16, HU-17, HU-19, HU-20, HU-21, HU-23.
- **Médico y administración:** HU-34, HU-35, HU-36, HU-37.

El resto (lista de espera, pagos en línea, mensajería, PQRS, recordatorios de medicamentos, reportes, etc.) se puede entregar en fases posteriores.

## Requisitos transversales

No están en la lista original de requerimientos, pero se recomienda contemplarlos desde el diseño:

- **Protección de datos personales:** Ley 1581 de 2012 y normativa de tratamiento de datos sensibles.
- **Historia clínica:** Resolución 1995 de 1999 y Ley 2015 de 2020 (interoperabilidad).
- **Seguridad:** cifrado en tránsito y en reposo, control de acceso por rol, auditoría de accesos y copias de seguridad.
- **Disponibilidad y rendimiento:** definir metas de disponibilidad y tiempos de respuesta.
- **Accesibilidad:** pautas WCAG, pensando en adultos mayores y personas con discapacidad.
- **Pagos:** uso de pasarela certificada, sin almacenar datos completos de tarjetas.

## Estructura del repositorio



## Próximos pasos

1. Validar prioridades y alcance del MVP con los interesados.
2. Estimar las historias (puntos de historia o tamaño de camiseta).
3. Definir arquitectura, stack tecnológico e integraciones (EPS, laboratorios, pasarela de pagos, telemedicina).
4. Diseñar prototipos de las pantallas principales.
5. Planificar los sprints a partir del backlog.

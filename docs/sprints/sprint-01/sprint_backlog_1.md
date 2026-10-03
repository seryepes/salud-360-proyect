# product backlong - salud 360

# Requerimientos: sistema de salud para pacientes
# Requerimientos funcionales

1. Registro y autenticación

RF-01: Registro de paciente con datos personales (documento, nombre, fecha de nacimiento, contacto, EPS o aseguradora).
RF-02: Inicio de sesión con correo y contraseña.
RF-03: Recuperación de contraseña por correo o SMS.
RF-04: Verificación de identidad en dos pasos (opcional, recomendada).
RF-05: Edición del perfil y de los datos de contacto.
RF-06: Gestión de grupo familiar (dependientes como hijos o adultos mayores).

2. Gestión de citas médicas

RF-07: Consulta de especialidades, médicos y sedes disponibles.
RF-08: Consulta de la disponibilidad de agenda por médico, fecha y sede.
RF-09: Solicitud de cita médica.
RF-10: Reprogramación y cancelación de citas, con un plazo mínimo configurable.
RF-11: Confirmación de la cita por correo, SMS o notificación push.
RF-12: Recordatorios automáticos antes de la cita (por ejemplo 24 h y 2 h antes).
RF-13: Historial de citas (pasadas, próximas y canceladas).
RF-14: Lista de espera, con aviso cuando se libere un cupo.
RF-15: Soporte para citas presenciales y de telemedicina.

3. Historia clínica

RF-16: Visualización de la historia clínica del paciente (solo lectura).
RF-17: Consulta de diagnósticos, antecedentes, alergias y signos vitales.
RF-18: Consulta de evoluciones y notas de cada consulta.
RF-19: Visualización y descarga de resultados de laboratorio e imágenes diagnósticas.
RF-20: Consulta de fórmulas médicas y medicamentos prescritos.
RF-21: Consulta de órdenes médicas (exámenes, remisiones, incapacidades).
RF-22: Descarga de la historia clínica en PDF.
RF-23: Registro de quién accedió a la historia clínica y cuándo.

4. Medicamentos y órdenes

RF-24: Seguimiento de fórmulas vigentes y de su fecha de vencimiento.
RF-25: Recordatorio de toma de medicamentos.
RF-26: Solicitud de autorización de procedimientos, cuando aplique.

5. Notificaciones y comunicación

RF-27: Centro de notificaciones dentro de la aplicación.
RF-28: Envío de notificaciones por correo, SMS o push, según la preferencia del usuario.
RF-29: Mensajería segura entre paciente y personal de salud.
RF-30: Canal de peticiones, quejas, reclamos y sugerencias (PQRS).

6. Pagos y facturación

RF-31: Consulta de copagos y cuotas moderadoras.
RF-32: Pago en línea.
RF-33: Descarga de facturas y comprobantes.

7. Perfil de médico y personal administrativo

RF-34: El médico configura su agenda y su disponibilidad.
RF-35: El médico registra la consulta, el diagnóstico, la fórmula y las órdenes.
RF-36: El médico accede a la historia clínica de sus pacientes.
RF-37: El administrador gestiona usuarios, roles, especialidades y sedes.
RF-38: Reportes de citas, asistencia, cancelaciones y ocupación.

# epicas principales identificadas.
1. Registro y autenticación
2. Gestión de citas médicas
3. Historia clínica
4. Perfil de médico y personal administrativo


# historias de usuario:

## 1. Registro y autenticación

### HU-01 Registro de paciente (RF-01) — Prioridad: Alta
**Como** paciente nuevo, **quiero** registrarme con mi documento, nombre, fecha de nacimiento, datos de contacto y EPS o aseguradora, **para** acceder a los servicios de salud en línea.
**Criterios de aceptación:**
- El formulario exige tipo y número de documento, nombre, fecha de nacimiento, correo, teléfono y EPS/aseguradora.
- No permite registrar un documento ya existente en el sistema.
- Valida formato de correo y teléfono, y que el paciente tenga una edad válida.
- Al finalizar, el sistema envía un correo de verificación y la cuenta queda activa solo tras confirmarlo.
- El paciente debe aceptar la política de tratamiento de datos personales antes de registrarse.

### HU-02 Inicio de sesión (RF-02) — Prioridad: Alta
**Como** paciente registrado, **quiero** iniciar sesión con mi correo y contraseña, **para** acceder de forma segura a mi información.
**Criterios de aceptación:**
- Con credenciales válidas, el sistema da acceso a la página principal del paciente.
- Con credenciales inválidas, muestra un mensaje genérico sin revelar cuál dato falló.
- Tras un número configurable de intentos fallidos, la cuenta se bloquea temporalmente.
- La sesión expira por inactividad después de un tiempo configurable.

### HU-03 Recuperación de contraseña (RF-03) — Prioridad: Alta
**Como** paciente que olvidó su contraseña, **quiero** recuperarla por correo o SMS, **para** volver a ingresar sin ayuda presencial.
**Criterios de aceptación:**
- El paciente elige el canal (correo o SMS) entre los registrados en su perfil.
- El enlace o código de recuperación expira en un tiempo definido y es de un solo uso.
- La nueva contraseña cumple las reglas de seguridad (longitud, mayúsculas, números).
- Tras el cambio, se cierran las demás sesiones activas y se notifica el cambio al paciente.

### HU-04 Verificación en dos pasos (RF-04) — Prioridad: Media
**Como** paciente, **quiero** activar la verificación en dos pasos, **para** proteger mi información clínica.
**Criterios de aceptación:**
- La opción se puede activar o desactivar desde el perfil, y el sistema la recomienda durante el registro.
- Al iniciar sesión con la opción activa, se solicita un código enviado por SMS, correo o aplicación autenticadora.
- Para desactivarla se exige confirmar la contraseña.
- El sistema ofrece códigos de respaldo por si el paciente pierde acceso al segundo factor.

### HU-05 Edición de perfil y contacto (RF-05) — Prioridad: Media
**Como** paciente, **quiero** editar mi perfil y mis datos de contacto, **para** mantener mi información actualizada.
**Criterios de aceptación:**
- Puedo modificar correo, teléfono, dirección y EPS/aseguradora.
- Documento y fecha de nacimiento no son editables directamente (requieren solicitud de corrección).
- Cambiar correo o teléfono exige verificar el nuevo dato.
- Se registra la fecha y el usuario de cada cambio.

### HU-06 Gestión de grupo familiar (RF-06) — Prioridad: Media
**Como** titular de cuenta, **quiero** agregar y gestionar a mis dependientes (hijos, adultos mayores), **para** administrar su atención desde mi cuenta.
**Criterios de aceptación:**
- Puedo agregar un dependiente con sus datos y su parentesco.
- Puedo alternar entre mi perfil y el de cada dependiente.
- Puedo solicitar citas y consultar historia clínica de mis dependientes, según los permisos otorgados.
- El sistema pide un soporte de autorización o parentesco cuando la norma lo requiere.
- Puedo desvincular a un dependiente en cualquier momento.
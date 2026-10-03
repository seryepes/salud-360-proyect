# Historias de usuario: Sistema de salud para pacientes

**Roles:** Paciente, Cuidador/Titular (gestiona dependientes), Médico, Administrador.
**Prioridad:** Alta / Media / Baja (propuesta inicial, ajustable con el equipo).
**Formato:** Como [rol], quiero [acción], para [beneficio]. Cada historia incluye criterios de aceptación.

---

## 1. Registro y autenticación

### HU-01 Registro de paciente (RF-01) — Prioridad: Alta
# Estimacion: 13
**Como** paciente nuevo, **quiero** registrarme con mi documento, nombre, fecha de nacimiento, datos de contacto y EPS o aseguradora, **para** acceder a los servicios de salud en línea.
**Criterios de aceptación:**
- El formulario exige tipo y número de documento, nombre, fecha de nacimiento, correo, teléfono y EPS/aseguradora.
- No permite registrar un documento ya existente en el sistema.
- Valida formato de correo y teléfono, y que el paciente tenga una edad válida.
- Al finalizar, el sistema envía un correo de verificación y la cuenta queda activa solo tras confirmarlo.
- El paciente debe aceptar la política de tratamiento de datos personales antes de registrarse.

### HU-02 Inicio de sesión (RF-02) — Prioridad: Alta
# Estimacion: 8
**Como** paciente registrado, **quiero** iniciar sesión con mi correo y contraseña, **para** acceder de forma segura a mi información.
**Criterios de aceptación:**
- Con credenciales válidas, el sistema da acceso a la página principal del paciente.
- Con credenciales inválidas, muestra un mensaje genérico sin revelar cuál dato falló.
- Tras un número configurable de intentos fallidos, la cuenta se bloquea temporalmente.
- La sesión expira por inactividad después de un tiempo configurable.

### HU-03 Recuperación de contraseña (RF-03) — Prioridad: Alta
# Estimacion: 8
**Como** paciente que olvidó su contraseña, **quiero** recuperarla por correo o SMS, **para** volver a ingresar sin ayuda presencial.
**Criterios de aceptación:**
- El paciente elige el canal (correo o SMS) entre los registrados en su perfil.
- El enlace o código de recuperación expira en un tiempo definido y es de un solo uso.
- La nueva contraseña cumple las reglas de seguridad (longitud, mayúsculas, números).
- Tras el cambio, se cierran las demás sesiones activas y se notifica el cambio al paciente.

### HU-04 Verificación en dos pasos (RF-04) — Prioridad: Media
# Estimacion: 6
**Como** paciente, **quiero** activar la verificación en dos pasos, **para** proteger mi información clínica.
**Criterios de aceptación:**
- La opción se puede activar o desactivar desde el perfil, y el sistema la recomienda durante el registro.
- Al iniciar sesión con la opción activa, se solicita un código enviado por SMS, correo o aplicación autenticadora.
- Para desactivarla se exige confirmar la contraseña.
- El sistema ofrece códigos de respaldo por si el paciente pierde acceso al segundo factor.

### HU-05 Edición de perfil y contacto (RF-05) — Prioridad: Media
# Estimacion: 2
**Como** paciente, **quiero** editar mi perfil y mis datos de contacto, **para** mantener mi información actualizada.
**Criterios de aceptación:**
- Puedo modificar correo, teléfono, dirección y EPS/aseguradora.
- Documento y fecha de nacimiento no son editables directamente (requieren solicitud de corrección).
- Cambiar correo o teléfono exige verificar el nuevo dato.
- Se registra la fecha y el usuario de cada cambio.

### HU-06 Gestión de grupo familiar (RF-06) — Prioridad: Media
# Estimacion: 2
**Como** titular de cuenta, **quiero** agregar y gestionar a mis dependientes (hijos, adultos mayores), **para** administrar su atención desde mi cuenta.
**Criterios de aceptación:**
- Puedo agregar un dependiente con sus datos y su parentesco.
- Puedo alternar entre mi perfil y el de cada dependiente.
- Puedo solicitar citas y consultar historia clínica de mis dependientes, según los permisos otorgados.
- El sistema pide un soporte de autorización o parentesco cuando la norma lo requiere.
- Puedo desvincular a un dependiente en cualquier momento.

---

## 2. Gestión de citas médicas

### HU-07 Consulta de especialidades, médicos y sedes (RF-07) — Prioridad: Alta
# Estimacion: 13
**Como** paciente, **quiero** consultar las especialidades, médicos y sedes disponibles, **para** elegir dónde y con quién atenderme.
**Criterios de aceptación:**
- Puedo filtrar por especialidad, médico, sede y modalidad (presencial o telemedicina).
- Se muestran solo los servicios cubiertos por mi EPS/aseguradora.
- Cada médico muestra nombre, especialidad y sedes de atención.
- Cada sede muestra dirección y datos de contacto.

### HU-08 Consulta de disponibilidad de agenda (RF-08) — Prioridad: Alta
# Estimacion: 13
**Como** paciente, **quiero** ver la disponibilidad de agenda por médico, fecha y sede, **para** escoger un horario que me convenga.
**Criterios de aceptación:**
- La agenda se muestra en formato calendario con los cupos libres y ocupados.
- Los cupos se actualizan en tiempo real.
- Si no hay disponibilidad, el sistema me ofrece la lista de espera (HU-14) o fechas cercanas.

### HU-09 Solicitud de cita (RF-09) — Prioridad: Alta
# Estimacion: 13
**Como** paciente, **quiero** solicitar una cita médica en un cupo disponible, **para** recibir atención sin desplazarme a asignarla.
**Criterios de aceptación:**
- Antes de confirmar, el sistema muestra un resumen (médico, fecha, hora, sede, modalidad y copago si aplica).
- Un cupo no puede ser asignado a dos pacientes a la vez.
- Se valida que el paciente no tenga otra cita en el mismo horario.
- Si el servicio requiere orden médica o autorización, el sistema lo indica y lo verifica.
- Al confirmar, la cita queda registrada en mi historial.

### HU-10 Reprogramación y cancelación de citas (RF-10) — Prioridad: Alta
# Estimacion: 6
**Como** paciente, **quiero** reprogramar o cancelar una cita, **para** ajustarla si no puedo asistir.
**Criterios de aceptación:**
- Solo puedo modificar la cita hasta el plazo mínimo configurable antes de su hora.
- Pasado ese plazo, el sistema informa que no es posible y muestra cómo comunicarse con la sede.
- Al cancelar, el cupo vuelve a quedar disponible (y se notifica a la lista de espera).
- Al reprogramar, solo se puede elegir un nuevo cupo disponible.
- Recibo una notificación de la cancelación o del cambio.

### HU-11 Confirmación de cita (RF-11) — Prioridad: Alta
# Estimacion: 6
**Como** paciente, **quiero** recibir la confirmación de mi cita por correo, SMS o notificación push, **para** tener la certeza de que quedó agendada.
**Criterios de aceptación:**
- La confirmación se envía en el momento en que se agenda la cita.
- Incluye médico, especialidad, fecha, hora, sede o enlace de telemedicina e indicaciones previas.
- Se envía por los canales que el paciente tenga habilitados.

### HU-12 Recordatorios automáticos (RF-12) — Prioridad: Alta
# Estimacion: 6
**Como** paciente, **quiero** recibir recordatorios antes de mi cita, **para** no olvidarla.
**Criterios de aceptación:**
- Se envían recordatorios 24 h y 2 h antes de la cita (tiempos configurables).
- No se envían recordatorios de citas canceladas o reprogramadas.
- El recordatorio incluye un acceso directo para confirmar, reprogramar o cancelar.

### HU-13 Historial de citas (RF-13) — Prioridad: Media
# Estimacion: 6
**Como** paciente, **quiero** ver mis citas pasadas, próximas y canceladas, **para** hacer seguimiento de mi atención.
**Criterios de aceptación:**
- Las citas se agrupan por estado (próximas, pasadas, canceladas).
- Puedo filtrar por fecha, especialidad y médico.
- Cada cita muestra su estado (asistida, no asistida, cancelada) y permite ver su detalle.
- Desde una cita próxima puedo reprogramarla o cancelarla.

### HU-14 Lista de espera (RF-14) — Prioridad: Media
# Estimacion: 6
**Como** paciente, **quiero** anotarme en una lista de espera, **para** recibir aviso si se libera un cupo antes.
**Criterios de aceptación:**
- Puedo inscribirme cuando no haya cupos para el médico, fecha o sede deseados.
- Al liberarse un cupo, recibo un aviso por mis canales de notificación.
- Tengo un tiempo limitado para aceptar el cupo; si no respondo, se ofrece al siguiente en la lista.
- Puedo salir de la lista cuando quiera, y el sistema me sale automáticamente si agendo otra cita equivalente.

### HU-15 Citas presenciales y de telemedicina (RF-15) — Prioridad: Alta
# Estimacion: 13
**Como** paciente, **quiero** elegir entre cita presencial o de telemedicina, **para** atenderme según mi disponibilidad y necesidad.
**Criterios de aceptación:**
- Al solicitar la cita puedo escoger la modalidad, solo si el médico la ofrece.
- Para telemedicina, el sistema genera un enlace de acceso a la videoconsulta, visible desde la cita.
- El enlace se habilita poco antes de la hora de la cita.
- El sistema informa los requisitos técnicos mínimos (cámara, micrófono, conexión).

---

## 3. Historia clínica

### HU-16 Visualización de historia clínica (RF-16) — Prioridad: Alta
# Estimacion: 13
**Como** paciente, **quiero** ver mi historia clínica en modo de solo lectura, **para** conocer mi información de salud.
**Criterios de aceptación:**
- Solo yo (o mis dependientes autorizados) puedo ver mi historia clínica.
- La información no se puede modificar desde la vista del paciente.
- La historia se organiza por secciones (diagnósticos, consultas, resultados, fórmulas, órdenes).

### HU-17 Diagnósticos, antecedentes, alergias y signos vitales (RF-17) — Prioridad: Alta
# Estimacion: 13
**Como** paciente, **quiero** consultar mis diagnósticos, antecedentes, alergias y signos vitales, **para** tener un resumen de mi estado de salud.
**Criterios de aceptación:**
- Los diagnósticos se muestran con fecha y médico que los registró.
- Las alergias se destacan visualmente.
- Los signos vitales (peso, talla, presión, frecuencia cardiaca, etc.) se muestran con su fecha y, cuando sea posible, su evolución en el tiempo.

### HU-18 Evoluciones y notas de consulta (RF-18) — Prioridad: Media
# Estimacion: 6
**Como** paciente, **quiero** consultar las evoluciones y notas de cada consulta, **para** recordar lo que se habló y las indicaciones dadas.
**Criterios de aceptación:**
- Cada consulta muestra fecha, médico, especialidad y notas.
- Se ordenan de la más reciente a la más antigua.
- Puedo buscar y filtrar por fecha o especialidad.

### HU-19 Resultados de laboratorio e imágenes (RF-19) — Prioridad: Alta
# Estimacion: 13
**Como** paciente, **quiero** ver y descargar mis resultados de laboratorio e imágenes diagnósticas, **para** conservarlos y compartirlos cuando los necesite.
**Criterios de aceptación:**
- Los resultados aparecen en el sistema cuando son publicados por el laboratorio o el servicio.
- Puedo visualizar el resultado en línea y descargarlo en un formato estándar (PDF, o formato de imagen según corresponda).
- Recibo una notificación cuando un nuevo resultado esté disponible.
- Cada resultado indica fecha, examen y entidad que lo emitió.

### HU-20 Fórmulas médicas y medicamentos (RF-20) — Prioridad: Alta
# Estimacion: 13
**Como** paciente, **quiero** consultar mis fórmulas médicas y los medicamentos prescritos, **para** saber qué debo tomar y en qué dosis.
**Criterios de aceptación:**
- Cada fórmula muestra medicamento, dosis, frecuencia, duración, fecha y médico prescriptor.
- Puedo ver el detalle de fórmulas anteriores.
- Puedo descargar o imprimir la fórmula.

### HU-21 Órdenes médicas (RF-21) — Prioridad: Alta
# Estimacion: 13
**Como** paciente, **quiero** consultar mis órdenes médicas (exámenes, remisiones, incapacidades), **para** saber qué trámites tengo pendientes.
**Criterios de aceptación:**
- Las órdenes se clasifican por tipo (exámenes, remisiones, incapacidades) y estado (pendiente, realizada, vencida).
- Cada orden muestra fecha de emisión, vigencia y médico que la emitió.
- Puedo descargar la orden o la incapacidad.

### HU-22 Descarga de historia clínica en PDF (RF-22) — Prioridad: Media
# Estimacion: 6
**Como** paciente, **quiero** descargar mi historia clínica en PDF, **para** tener una copia o presentarla en otra institución.
**Criterios de aceptación:**
- Puedo elegir el rango de fechas y las secciones que incluirá el documento.
- El PDF incluye datos del paciente, fecha de generación e identificación del documento.
- La descarga exige reautenticación o confirmación adicional por la sensibilidad de los datos.
- Cada descarga queda registrada en la auditoría de accesos.

### HU-23 Registro de accesos a la historia clínica (RF-23) — Prioridad: Alta
# Estimacion: 6
**Como** paciente, **quiero** ver quién accedió a mi historia clínica y cuándo, **para** controlar la privacidad de mis datos.
**Criterios de aceptación:**
- El registro muestra usuario, rol, fecha, hora y tipo de acceso (consulta, descarga).
- Los registros no se pueden editar ni eliminar.
- Puedo filtrar por fecha y por usuario.
- Si veo un acceso que no reconozco, puedo reportarlo mediante PQRS.

---

## 4. Medicamentos y órdenes

### HU-24 Seguimiento de fórmulas vigentes (RF-24) — Prioridad: Media
# Estimacion: 6
**Como** paciente, **quiero** ver mis fórmulas vigentes y su fecha de vencimiento, **para** reclamar o renovar mis medicamentos a tiempo.
**Criterios de aceptación:**
- Las fórmulas se clasifican en vigentes y vencidas.
- Cada fórmula vigente muestra los días restantes de vigencia.
- Recibo un aviso antes de que una fórmula venza (anticipación configurable).

### HU-25 Recordatorio de toma de medicamentos (RF-25) — Prioridad: Media
# Estimacion: 6
**Como** paciente, **quiero** configurar recordatorios para tomar mis medicamentos, **para** cumplir mi tratamiento.
**Criterios de aceptación:**
- Puedo crear recordatorios a partir de una fórmula, con dosis, horario y duración.
- Recibo notificaciones push o SMS a la hora configurada.
- Puedo marcar la toma como realizada, posponerla u omitirla.
- Puedo pausar o eliminar un recordatorio.

### HU-26 Solicitud de autorización de procedimientos (RF-26) — Prioridad: Media
# Estimacion: 6
**Como** paciente, **quiero** solicitar la autorización de un procedimiento cuando aplique, **para** que mi EPS o aseguradora lo apruebe sin trámites presenciales.
**Criterios de aceptación:**
- Puedo iniciar la solicitud desde una orden médica que requiera autorización.
- Puedo adjuntar los documentos de soporte necesarios.
- La solicitud tiene un estado visible (radicada, en estudio, aprobada, rechazada).
- Recibo una notificación cada vez que cambie el estado, y si es rechazada veo el motivo.

---

## 5. Notificaciones y comunicación

### HU-27 Centro de notificaciones (RF-27) — Prioridad: Media
# Estimacion: 2
**Como** paciente, **quiero** un centro de notificaciones dentro de la aplicación, **para** ver en un solo lugar los avisos importantes.
**Criterios de aceptación:**
- Las notificaciones se listan por fecha y distinguen las leídas de las no leídas.
- Puedo marcar como leída, eliminar y filtrar por tipo (citas, resultados, pagos, mensajes).
- Un indicador muestra la cantidad de notificaciones sin leer.

### HU-28 Preferencias de notificación (RF-28) — Prioridad: Media
# Estimacion: 2
**Como** paciente, **quiero** elegir si recibo notificaciones por correo, SMS o push, **para** que me lleguen por el medio que prefiero.
**Criterios de aceptación:**
- Puedo activar o desactivar cada canal por tipo de notificación.
- El sistema respeta mis preferencias en todos los envíos.
- Las notificaciones críticas (por ejemplo, seguridad de la cuenta) no se pueden desactivar por completo.

### HU-29 Mensajería segura (RF-29) — Prioridad: Media
# Estimacion: 2
**Como** paciente, **quiero** enviar mensajes seguros a mi personal de salud, **para** resolver dudas sin ir a una consulta.
**Criterios de aceptación:**
- Solo puedo escribir a profesionales con los que he tenido atención.
- Los mensajes se transmiten y almacenan cifrados.
- Puedo adjuntar archivos permitidos (imágenes, PDF) con un tamaño máximo.
- Veo el estado del mensaje (enviado, leído) y recibo notificación de la respuesta.
- El sistema muestra un aviso de que no es un canal para urgencias.

### HU-30 PQRS (RF-30) — Prioridad: Media
# Estimacion: 2
**Como** paciente, **quiero** radicar peticiones, quejas, reclamos y sugerencias, **para** manifestar mi inconformidad o mis ideas de mejora.
**Criterios de aceptación:**
- Puedo seleccionar el tipo de solicitud, describirla y adjuntar soportes.
- Al radicar, recibo un número de radicado.
- Puedo consultar el estado y la respuesta de mi PQRS.
- El sistema alerta a los responsables cuando se acerque el plazo legal de respuesta.

---

## 6. Pagos y facturación

### HU-31 Consulta de copagos y cuotas moderadoras (RF-31) — Prioridad: Media
# Estimacion: 18
**Como** paciente, **quiero** consultar los copagos y cuotas moderadoras que debo pagar, **para** saber cuánto cuesta mi atención antes de asistir.
**Criterios de aceptación:**
- El valor se calcula según mi EPS/aseguradora y mi régimen o categoría.
- Se muestra el valor antes de confirmar la cita.
- Puedo ver los pagos pendientes y los pagos realizados.

### HU-32 Pago en línea (RF-32) — Prioridad: Media
# Estimacion: 6
**Como** paciente, **quiero** pagar mis copagos y cuotas en línea, **para** evitar filas y trámites en la sede.
**Criterios de aceptación:**
- Puedo pagar con los medios disponibles (tarjeta, PSE, otros).
- El pago se procesa mediante una pasarela segura y el sistema no almacena datos completos de tarjeta.
- Recibo confirmación inmediata del pago, exitoso o rechazado.
- Si el pago falla, la cita no se pierde y puedo reintentar dentro de un plazo definido.

### HU-33 Facturas y comprobantes (RF-33) — Prioridad: Media
# Estimacion: 6
**Como** paciente, **quiero** descargar mis facturas y comprobantes de pago, **para** tener soporte de mis transacciones.
**Criterios de aceptación:**
- Cada pago genera un comprobante descargable en PDF.
- Puedo buscar por fecha o por concepto.
- La factura cumple los requisitos de facturación vigentes en Colombia.

---

## 7. Perfil de médico y personal administrativo

### HU-34 Configuración de agenda del médico (RF-34) — Prioridad: Alta
# Estimacion: 13
**Como** médico, **quiero** configurar mi agenda y mi disponibilidad, **para** que los pacientes agenden en los horarios que puedo atender.
**Criterios de aceptación:**
- Puedo definir días, horarios, duración de cada consulta, sede y modalidad (presencial o telemedicina).
- Puedo bloquear horarios (vacaciones, permisos, reuniones).
- Si modifico la agenda y hay citas afectadas, el sistema me avisa y notifica a los pacientes.
- No se permite crear horarios que se solapen.

### HU-35 Registro de consulta, diagnóstico, fórmula y órdenes (RF-35) — Prioridad: Alta
# Estimacion: 13
**Como** médico, **quiero** registrar la consulta, el diagnóstico, la fórmula y las órdenes, **para** dejar constancia de la atención y que el paciente la consulte.
**Criterios de aceptación:**
- Puedo registrar motivo de consulta, evolución, diagnóstico (con codificación estándar, por ejemplo CIE-10), fórmulas y órdenes.
- Al cerrar la consulta, el registro queda firmado y no editable; las correcciones se hacen mediante notas aclaratorias.
- El sistema advierte sobre las alergias registradas del paciente al formular.
- La información queda disponible para el paciente en su historia clínica.

### HU-36 Acceso del médico a la historia clínica (RF-36) — Prioridad: Alta
# Estimacion: 6
**Como** médico, **quiero** acceder a la historia clínica de mis pacientes, **para** tomar decisiones clínicas informadas.
**Criterios de aceptación:**
- Solo puedo acceder a la historia de pacientes que atiendo o tengo asignados.
- Cada acceso queda registrado en la auditoría (RF-23).
- Puedo ver el historial completo: diagnósticos, antecedentes, alergias, resultados, fórmulas y órdenes.

### HU-37 Gestión administrativa (RF-37) — Prioridad: Alta
# Estimacion: 13
**Como** administrador, **quiero** gestionar usuarios, roles, especialidades y sedes, **para** mantener la operación del sistema organizada y segura.
**Criterios de aceptación:**
- Puedo crear, editar, activar y desactivar usuarios.
- Puedo asignar roles con permisos diferenciados (paciente, médico, administrador).
- Puedo crear y editar especialidades y sedes y asignar médicos a ellas.
- Los cambios quedan registrados en una bitácora de auditoría.
- No puedo eliminar registros con información asociada (citas o historias); solo desactivarlos.

### HU-38 Reportes de gestión (RF-38) — Prioridad: Media
# Estimacion: 6
**Como** administrador, **quiero** generar reportes de citas, asistencia, cancelaciones y ocupación, **para** evaluar y mejorar la operación.
**Criterios de aceptación:**
- Puedo filtrar por rango de fechas, sede, especialidad y médico.
- Los reportes incluyen total de citas, porcentaje de asistencia, de inasistencia y de cancelación, y ocupación de agenda.
- Puedo exportarlos a Excel o PDF.
- Los reportes no muestran información clínica individual de los pacientes.

---

## Notas generales
- **Requisitos transversales sugeridos** (no incluidos en la lista original): cumplimiento de la Ley 1581 de 2012 (protección de datos) y de la normativa colombiana sobre historia clínica (Resolución 1995 de 1999 y Ley 2015 de 2020), cifrado de datos en tránsito y en reposo, disponibilidad y accesibilidad (WCAG).
- **Sugerencia de priorización para el MVP:** HU-01, 02, 03, 07 a 12, 15, 16, 17, 19, 20, 21, 23, 34, 35, 36 y 37.
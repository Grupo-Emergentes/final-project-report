# Links
- Prototipo hecho por la IA de figma: https://www.figma.com/make/JkXGNcx9THDL9M0mjAqYer/Recrear-app-Diia-web?node-id=0-1&t=LSr3e4zArI9tBnOH-1
- Trabajo de IoT mio si les sirve: https://github.com/Los-Angelitos/final-project-report/tree/main
- Link del trello: https://trello.com/invite/b/68b9c5c222441556071afd6e/ATTIe087d42e2a95ee2ea2154950f84bf30512E977FD/arquitectura-de-software-emergentes

# Información Relevante

## 1) Resumen 

Qué es: Plataforma web única para que la ciudadanía gestione documentos personales digitales (billetera) y trámites con entidades públicas.
Problema que resuelve: Fragmentación de portales, procesos engorrosos, validación de documentos poco confiable y poca trazabilidad.
Cómo lo resuelve:
	•	Billetera ciudadana con DNI digital, licencia de conducir, certificado COVID, RUC, etc., respaldados criptográficamente (blockchain para integridad y verificación).
	•	Catálogo unificado de trámites por entidad (RENIEC, SUNAT, MTC, MINEDU, MINSA, Municipalidades, MTPE, Poder Judicial).
	•	Funcionalidades extra: chatbot IA, notificaciones, gestión de perfil, registro/login.

## 2) Antecedentes / Contexto  
	•	Contexto local (Perú):
	•	Entidades con portales y experiencias heterogéneas (RENIEC, SUNAT, MTC, etc.).
	•	Ciudadanía enfrenta fricción (múltiples cuentas, requisitos, colas, desconocimiento de estado de trámite).
	•	Oportunidad: Unificar acceso, estandarizar UX, y proveer documentos verificables (códigos QR firmados + hash en blockchain) que faciliten control, fiscalización y servicio.
	•	Hipótesis de valor:
	1.	Reducir tiempo y errores en trámites.
	2.	Aumentar confianza al usar documentos digitales validados.
	3.	Disminuir costos operativos para el Estado con procesos más trazables y medibles.

## 3) Concepto del Producto / Servicio

Propuesta: “Tu Estado en un solo lugar”.
	•	Billetera documentaria: Visualiza documentos digitales con estado, vigencia y metadatos (emisor, fecha emisión, vencimiento). 
 Cada documento tiene QR verificable; el QR lleva a una página de verificación con hash y sello de tiempo (on-chain / notarización).
	•	Servicios por entidad: El usuario explora trámites disponibles por organismo (RENIEC, SUNAT, etc.). Cada trámite tiene ficha: requisitos, costos, 
 tiempo estimado, pasos, estado en tiempo real.
	•	Pre-verificación de identidad de ambos contrayentes.
	•	Agendamiento de videollamada con verificación de presencia, lectura de acta, y registro.
	•	Generación de constancia digital y envío a la billetera (con QR).
	•	Soporte IA (chatbot): Explica requisitos, guía pasos, sugiere correcciones.
	•	Notificaciones: Estados de trámites, vencimientos (ej. licencia), alertas de actividad.
	•	Gestión de perfil: Datos personales básicos, medios de contacto, factores de autenticación.

Para funcionarios (visión inicial):
	•	Admin central (Ministerio de Transformación Digital): crea/gestiona roles por entidad, define permisos, ve tableros macro (volumen de trámites por entidad, SLA, colas).
	•	Coordinador de entidad (ej. RENIEC / SUNAT): administra catálogos de trámites de su entidad, reasigna casos, ve colas, KPIs locales.
	•	Accesos siempre mínimos necesarios (principio de least privilege).
	•	Bitácora/Auditoría: toda acción queda registrada para trazabilidad.

⸻

## 4) Usuarios / Público Objetivo

Segmento 1 – Ciudadanía (primario):
	•	Necesidades: centralizar documentos, completar trámites rápido, saber qué falta y en qué estado está todo.
	•	Dolencias: portales dispersos, contraseñas múltiples, requisitos poco claros, validación poco confiable.
	•	Momentos clave: renovar DNI, cambio de domicilio, registrar nacimiento, consultar estado tributario, emitir comprobante, mostrar un documento válido (QR).

Segmento 2 – Funcionarios públicos (secundario):
	•	Necesidades: verificar documentos, gestionar colas/casos, estandarizar criterios, medir tiempos, reducir fraudes.
	•	Dolencias: herramientas dispares, poca trazabilidad, duplicidad de captura de datos, dificultad para seguir SLA.


## 5) Flujo General / Arquitectura Funcional

Flujo alto nivel (ciudadano):

[Registro/Login con MFA]
   ↓
[Home Usuario]
   ├─ Billetera (Documentos)
   │    ├─ DNI digital (ver + QR)
   │    ├─ Licencia conducir
   │    ├─ Certificado COVID
   │    └─ RUC (estado)
   ├─ Trámites por Entidad
   │    ├─ RENIEC (acta, registro nacimiento, renovar DNI, cambio domicilio)
   │    └─ SUNAT (estado tributario, emitir comprobante)
   ├─ Chatbot IA (ayuda)
   ├─ Notificaciones
   └─ Perfil (datos + seguridad)

Flujo alto nivel (funcionario):

[Login Funcionario con MFA]
   ↓
[Dashboard según rol]
   ├─ Bandeja de trámites (asignados / cola)
   ├─ Verificación de documentos (escaneo/ingreso QR)
   ├─ Gestión de catálogo de trámites (según permisos)
   ├─ Métricas/KPIs (volumen, tiempos, SLA)
   └─ Auditoría (según rol)

Lógica funcional clave:
	•	QR verificable: QR → endpoint de verificación → muestra “válido / expirado / revocado” + metadatos; referencia a hash on-chain.
	•	Estados de trámite: borrador → presentado → en revisión → observado → aprobado/rechazado → cerrado, con notificaciones en cada transición.
	•	Chatbot IA: FAQ + guía paso a paso; si detecta atasco, sugiere abrir trámite o subir requisito faltante.
	•	Roles y permisos: Admin central define scopes por entidad; funcionarios ven solo lo que necesitan.
	•	Auditoría end-to-end: cada acción (ciudadano/funcionario) registra quién, qué, cuándo y dónde.

⸻

## 6) Diseño de Interfaces / Vistas (descrito, sin mockups)

7.1. Home (ciudadano):
	•	Header: logo, acceso a Billetera, Trámites, Notificaciones, Perfil.
	•	Hero/Resumen: “Tus documentos y trámites en un solo lugar”.
	•	Tarjetas rápidas: DNI digital, SUNAT – Estado, RENIEC – Renovar DNI, Matrimonio por videollamada.
	•	Bloque “Continuar donde lo dejaste”: últimos trámites en progreso.
	•	Sección “Entidades”: grilla con RENIEC, SUNAT, MTC, etc.

7.2. Billetera:
	•	Lista de documentos con estado (vigente/por vencer/vencido), última actualización, botón “Mostrar QR”.
	•	Filtro por tipo y vigencia.
	•	Al abrir un documento: vista detallada con metadatos, QR, y botón “Compartir verificación”.

7.3. Catálogo de trámites (por entidad):
	•	Buscador + filtros (entidad, tipo de trámite, requisitos, tiempo estimado).
	•	Tarjetas de trámites con descripción breve, requisitos, tiempo, costo y botón Iniciar.

7.4. Flujo de trámite (ej. Renovar DNI):
	•	Paso 1: requisitos (checklist interactivo).
	•	Paso 2: datos pre-cargados (editable si procede).
	•	Paso 3: validación/adjuntos.
	•	Paso 4: Resumen + Enviar.
	•	Post-envío: tracking con línea de tiempo y notificaciones.

7.5. Matrimonio por videollamada:
	•	Wizard con: validación identidad de ambos, selección de fecha, verificación de requisitos, sala de videollamada segura, firma/constancia digital.
	•	Resultado: constancia se envía a Billetera.

7.6. Perfil y seguridad:
	•	Datos personales, MFA, dispositivos confiables, gestión de consentimiento de datos.

7.7. Funcionario (por rol):
	•	Dashboard: métricas clave (hoy/semana), cola por prioridad.
	•	Bandeja de casos: filtros (estado, entidad, SLA), vista de detalle del expediente.
	•	Verificador QR: input/cámara → resultado de validez + metadatos.
	•	Gestor de trámites (coordinador): alta/baja/edición de fichas, SLAs, textos guía.
	•	Auditoría: consultas por usuario, trámite, fecha; exportaciones controladas.

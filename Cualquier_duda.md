# Links
- **Prototipo hecho por la IA de Figma**: [Figma](https://www.figma.com/make/JkXGNcx9THDL9M0mjAqYer/Recrear-app-Diia-web?node-id=0-1&t=LSr3e4zArI9tBnOH-1)
- **Trabajo de IoT (propio)**: [GitHub](https://github.com/Los-Angelitos/final-project-report/tree/main)
- **Link del Trello**: [Trello](https://trello.com/invite/b/68b9c5c222441556071afd6e/ATTIe087d42e2a95ee2ea2154950f84bf30512E977FD/arquitectura-de-software-emergentes)

# Información Relevante

## 1) Resumen

- **Qué es**: Plataforma web única para que la ciudadanía gestione documentos personales digitales (billetera) y trámites con entidades públicas.
- **Problema que resuelve**: Fragmentación de portales, procesos engorrosos, validación de documentos poco confiable y poca trazabilidad.
- **Cómo lo resuelve**:
  - Billetera ciudadana con DNI digital, licencia de conducir, certificado COVID, RUC, etc., respaldados criptográficamente (blockchain para integridad y verificación).
  - Catálogo unificado de trámites por entidad (RENIEC, SUNAT, MTC, MINEDU, MINSA, Municipalidades, MTPE, Poder Judicial).
  - Funcionalidades extra: chatbot IA, notificaciones, gestión de perfil, registro/login.

## 2) Antecedentes

- **Contexto local (Perú)**:
  - Entidades con portales y experiencias heterogéneas (RENIEC, SUNAT, MTC, etc.).
  - Ciudadanía enfrenta fricción (múltiples cuentas, requisitos, colas, desconocimiento de estado de trámite).
  - **Oportunidad**: Unificar acceso, estandarizar UX, y proveer documentos verificables (códigos QR firmados + hash en blockchain) que faciliten control, fiscalización y servicio.

- **Hipótesis de valor**:
  1. Reducir tiempo y errores en trámites.
  2. Aumentar confianza al usar documentos digitales validados.
  3. Disminuir costos operativos para el Estado con procesos más trazables y medibles.

## 3) Funcionalidades

**Propuesta: “Tu Estado en un solo lugar”.**

- **Billetera documentaria**: Visualiza documentos digitales con estado, vigencia y metadatos (emisor, fecha de emisión, vencimiento). Cada documento tiene QR verificable con página de verificación (hash + sello de tiempo).
- **Servicios por entidad**: Catálogo de trámites (RENIEC, SUNAT, etc.) con fichas detalladas: requisitos, costos, duración, pasos, estado en tiempo real.
- **Trámite de matrimonio por videollamada**:
  - Pre-verificación de identidad.
  - Agendamiento, verificación de presencia, lectura de acta, registro.
  - Generación de constancia digital y envío a billetera (con QR).
- **Soporte IA (chatbot)**: Guía de pasos, explicación de requisitos, sugerencias de corrección.
- **Notificaciones**: Cambios de estado, vencimientos, alertas.
- **Gestión de perfil**: Datos personales, contacto, autenticación.

**Para funcionarios públicos**:
- **Principio de mínimo privilegio**: Accesos según función.
- **Visualización de métricas clave en tarjetas**: Puede visualizar los dnis digitales, partidas, verificaciones y solicitudes realizadas. Con comparativa con el rendimiento del dia anterior. Filtrado de datos por rango de timepo o región. 
- **Visualización de Rendimiento por región**: Indicador de eficiencia operativa por región (Lima, Arequipa, Cusco, Piura).
- **Actividad en tiempo real**: Últimos eventos realizados por funcionarios (tipo de acción, persona, lugar, hora)
- **Visualización de tablas**: Con Lista con todos los documentos emitidos, ciudadanos con tramites recientes, oficinas de dicha entidad, reportes, auditorías, configuración

## 4) Usuarios / Público Objetivo

### Segmento 1 – Ciudadanía (primario):

- **Necesidades**: Centralizar documentos, trámites rápidos, visibilidad del estado de todo.
- **Dolencias**: Portales dispersos, múltiples contraseñas, poca claridad, validación poco confiable.
- **Momentos clave**: Renovación de DNI, cambio de domicilio, nacimiento, estado tributario, comprobantes, verificación de documentos.

### Segmento 2 – Funcionarios públicos (secundario):

- **Necesidades**: Verificación de documentos, gestión de trámites y colas, estandarización, trazabilidad.
- **Dolencias**: Herramientas dispares, duplicidad de datos, dificultad para cumplir SLA.

## 5) Diseño de Interfaces / Vistas

### 7.1. Home (Ciudadano)

- **Header**: Acceso a Billetera, Trámites, Notificaciones, Perfil.
- **Hero**: “Tus documentos y trámites en un solo lugar”.
- **Tarjetas rápidas**: DNI, SUNAT, RENIEC, Matrimonio.
- **Continuar donde lo dejaste**: Trámites en curso.
- **Entidades**: Grilla con RENIEC, SUNAT, MTC, etc.

### 7.2. Billetera

- Lista de documentos: estado (vigente/por vencer/vencido), última actualización, botón “Mostrar QR”.
- Filtros: por tipo, vigencia.
- Vista detallada: metadatos, QR, botón “Compartir verificación”.

### 7.3. Catálogo de trámites (por entidad)

- Buscador y filtros (entidad, tipo, requisitos, duración).
- Tarjetas con descripción, requisitos, tiempo, costo, botón Iniciar.

### 7.4. Flujo de trámite (ej. Renovar DNI)

- Paso 1: Requisitos (checklist interactivo).
- Paso 2: Datos pre-cargados (editable).
- Paso 3: Validación / adjuntos.
- Paso 4: Resumen + envío.
- Post-envío: Seguimiento con línea de tiempo y notificaciones.

### 7.5. Matrimonio

- Flujo guiado: validación de identidad, selección de fecha, requisitos, videollamada segura, firma digital.
- Resultado: Constancia enviada a billetera.

### 7.6. Perfil y seguridad

- Gestión de datos personales, MFA, dispositivos, consentimiento de datos.

### 7.7. Funcionario (por rol)

- **Dashboard**: KPIs diarios/semanales, colas por prioridad.
- **Bandeja de casos**: Filtros por estado, entidad, SLA.
- **Verificador QR**: Entrada manual o cámara → Validación + metadatos.
- **Gestión de trámites**: Alta/baja/edición, SLAs, textos guía.
- **Auditoría**: Búsqueda por usuario, trámite, fecha; exportaciones controladas.

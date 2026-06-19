🚪 Control de Acceso – App Web
Aplicación web para la gestión de acceso de proveedores y visitantes, control de citas, generación de QR, vales y reportes en tiempo real. Diseñada con enfoque offline-first, roles múltiples y control de seguridad.

📌 Descripción
Control de Acceso es una solución integral para:

Registro y gestión de citas (proveedores y visitantes)
Control de entradas, salidas y dictámenes de calidad
Generación y escaneo de códigos QR
Administración de vales (activos y personal)
Reportes y KPIs operativos
Control de usuarios con permisos por rol

Incluye sincronización con la nube y funcionamiento parcialmente offline.

🚀 Características Principales
✅ Gestión de Citas

Crear citas para proveedores o visitantes
Agenda visual por horario y área
Validación de disponibilidad por capacidad
Manejo de estados:

Programado
Llegado
Dentro
Despachado
Finalizado
Cancelado




📱 QR y Control de Acceso

Generación automática de QR por cita
Escaneo desde el módulo de guardia
Bloqueo automático por retraso (>30 min)
Reactivación de QR (con PIN admin)


🏭 Gestión por Áreas

Áreas configuradas:

Aduana piel
Aduana Exótico
Aduana Peleteria
Avíos
Otros


Capacidad simultánea configurable por área
Slots de agenda cada 30 minutos


📊 Dashboard y KPIs

Métricas en tiempo real:

Total de visitas
Tiempo promedio por área
% rechazo (calidad)
Incidencias
Puntualidad (a tiempo, tarde, no show)


Gráficos con Chart.js:

Visitas por área
Estado de citas
Dictamen de calidad
Incidencias
Puntualidad




📄 Facturas y Órdenes de Compra

Editor visual de relaciones Factura ↔ OC
Validaciones:

Máximo 8 OC por factura
5 caracteres por OC


Visualización estructurada


🧑‍💼 Roles y Permisos
Roles soportados:

Admin
Coordinador
Jefe / Jefe Compras
Compras
Guardia
Calidad
Contraloría
Anfitrión
Proveedor
Pendiente

✔ Cada rol tiene permisos específicos como:

Crear citas
Escanear QR
Dictaminar calidad
Autorizar vales
Exportar datos
Administración de usuarios


💼 Vales
Vales de Activos

Generación, autorización y seguimiento
Estados:

Generado
Pendiente
Fuera
Regreso / Cancelado



Vales de Personal

Control de salida e ingreso
Tiempo autorizado
Registro de excedentes


🛡 Seguridad

Autenticación con Firebase Auth
Control por roles y permisos
PIN de seguridad para acciones críticas
Auditoría de cambios en citas
Gestión de sesiones activas


📦 Persistencia y Sincronización

Base de datos en Firebase Firestore
Caché local con LocalStorage
Estrategia offline-first
Sincronización automática por TTL


📤 Exportación

Exportación a:

📊 Excel (hoy o acumulado)
🧾 PDF


Reportes filtrables por fecha y área


🧾 Reportes

Historial completo de visitas
Auditoría de cambios
Incidencias de calidad
Llegadas tarde y no show


📱 UI / UX

Diseño responsive
Sidebar colapsable
Tema oscuro / claro
Notificaciones tipo toast
Modal dialogs para acciones críticas


🧰 Tecnologías Utilizadas


Frontend

HTML5
CSS3 (responsive + themes)
JavaScript (Vanilla)



Librerías

Chart.js
QRCode.js
html5-qrcode
XLSX-js-style
html2canvas



Backend

Firebase

Authentication
Firestore Database






📂 Estructura General
/index.html          → App principal
/manifest.json       → Configuración PWA
/icon-192.png        → Ícono app


🔌 Funcionalidad Offline

Almacenamiento local de datos
Sincronización automática cuando vuelve la conexión
Indicador visual de estado de red


⚙️ Instalación

Clonar repositorio
Configurar Firebase:

API Key
Project ID


Abrir index.html en navegador


👨‍💻 Autor
Desarrollado por: Hermenegildo Perez

📄 Licencia
Uso interno / privado (puedes ajustar según tu uso).

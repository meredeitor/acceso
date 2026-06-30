# Control de Acceso Unificado

Aplicacion PWA para control operativo de accesos, citas, vales, bitacora de guardias y rondines de seguridad.

Version actual visible en la app: `proveedores-v65`.

## Modulos principales

- Proveedores: registro, autorizacion, entrada, salida y trazabilidad.
- Visitantes: registro de visitantes, anfitrion, motivo, entrada y salida.
- Citas: agenda para proveedores y visitantes.
- Vales de salida de activo: flujo de solicitud, autorizacion y salida.
- Vales de salida de personal: registro y seguimiento.
- Bitacora de novedades: registro operativo de guardias.
- Rondinero: rondines digitales mediante codigos QR.
- Configuracion: usuarios, roles, permisos y catalogos.

## Tecnologia

- HTML, CSS y JavaScript en una sola app principal.
- Firebase Authentication para sesiones.
- Firebase Firestore como base de datos.
- Service Worker y Manifest para funcionamiento PWA.
- Codigos QR para puntos de rondin y tarjetas de guardia.

Archivos principales:

- `index.html`: interfaz, estilos y logica principal.
- `service-worker.js`: cache PWA.
- `manifest.json`: configuracion de instalacion.
- `reglas.txt`: reglas sugeridas para Firestore.

## Roles

La app contempla roles operativos como:

- Administrador
- Coordinador / Supervisor
- Guardia
- Compras
- Jefe de compras
- Anfitrion
- Jefe
- Calidad
- Contraloria
- Proveedor

Los permisos se controlan desde la configuracion de usuarios y desde las reglas de Firestore.

## Rondinero

El modulo Rondinero permite ejecutar rondines de seguridad por medio de puntos de control con QR.

Flujo administrativo:

1. El administrador o supervisor registra puntos de control.
2. Cada punto tiene nombre, ubicacion, descripcion y codigo QR.
3. Se crean rutas con los puntos que debe visitar el guardia.
4. Desde Configuracion > Usuarios se puede generar el `QR Guardia`.
5. El administrador puede consultar historial, cumplimiento, avance y detalle de recorridos.

Flujo del guardia:

1. El guardia entra a `Mi rondin` desde su sidebar.
2. Antes de iniciar, escanea su tarjeta `QR Guardia`.
3. Selecciona la ruta asignada.
4. Inicia el rondin.
5. Escanea los QR de los puntos visitados.
6. Puede reportar novedades durante el recorrido.
7. Cierra el rondin al finalizar.

El rondinero guarda:

- Guardia identificado por QR.
- Usuario de la tablet que tenia la sesion abierta.
- Fecha y hora.
- Punto de control.
- Ubicacion.
- Estatus.
- Observaciones.
- Novedades reportadas.
- Tiempo total y avance del recorrido.

Nota: el modulo no guarda fotos ni videos para evitar saturar Firebase.

## Uso compartido de tablet

En caseta puede existir una sesion fija abierta en la misma tablet. Para identificar al guardia real, la app usa una tarjeta QR por guardia.

Esto aplica en:

- Rondinero.
- Bitacora de novedades.

Cuando el guardia escanea su QR, el sistema registra dos identidades:

- Guardia real: quien ejecuta el rondin o registra la novedad.
- Operador de sesion: usuario que esta autenticado en la tablet.

## Citas

La agenda de nuevas citas no permite generar citas a las 5:00 pm o despues.

Reglas actuales:

- Los horarios de 5:00 pm y 5:30 pm no se muestran.
- No se puede crear una cita a las 5:00 pm o despues.
- No se puede editar una cita para dejarla a las 5:00 pm o despues.

## Colecciones Firestore

Colecciones principales usadas por la app:

- `users`
- `proveedores`
- `visitas`
- `vales_activos`
- `vales_personal`
- `bitacora_guardia`
- `presence`
- `resumen_diario`
- `rondinero_puntos`
- `rondinero_rutas`
- `rondinero_rondines`
- `rondinero_eventos`

## Reglas de Firestore

Las reglas deben publicarse manualmente en Firebase Console tomando como base `reglas.txt`.

Puntos importantes:

- Rondinero debe permitir que el guardia trabaje con la sesion de la tablet mediante `operadorUid`.
- Bitacora debe permitir guardar novedades cuando el usuario autenticado sea el operador de sesion.
- Administrador y supervisor conservan acceso de consulta y seguimiento.

Si aparece `FirebaseError: Missing or insufficient permissions`, revisar primero:

- Que `reglas.txt` este publicado en Firebase.
- Que el usuario tenga el rol y permisos correctos.
- Que el documento guarde `operadorUid` igual al usuario autenticado.
- Que la tarjeta QR del guardia sea valida.

## PWA y cache

Cuando se modifique `index.html`, tambien se debe actualizar:

1. La version visible en el sidebar.
2. `CACHE_NAME` en `service-worker.js`.

Esto fuerza a los equipos a descargar la nueva version de la app.

Version actual:

- Sidebar: `proveedores-v65`
- Service Worker: `proveedores-v65`

## Mantenimiento recomendado

- Probar cambios como administrador y como guardia.
- Verificar que las reglas de Firestore esten publicadas despues de modificar permisos.
- Limpiar cache del navegador si una tablet sigue mostrando una version anterior.
- Mantener la version del sidebar y del service worker sincronizadas.
- Evitar cargar archivos pesados a Firebase desde rondines o bitacora.


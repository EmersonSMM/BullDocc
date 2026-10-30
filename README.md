# BullDocc · Generadores QA

28 generadores de datos y archivos para pruebas QA, reunidos en un HTML autocontenido.

## Descargar y utilizar

Descarga **BullDocc.html** desde [Releases](https://github.com/EmersonSMM/BullDocc/releases/latest) y ábrelo en tu navegador. Incluye estilos, imágenes, JSZip y PapaParse; la generación de archivos funciona localmente.

Las cinco nuevas variantes IPS (DNPA + MOVPER, DNP + MOVPER, DNP + pagos, DNPA + rebajas y DNP + pagos + MOVPER) llevan una banda diagonal **BETA**: «no se han testeado completamente». Su certificación funcional en SUCC está pendiente.

El nombre de descarga es **BullDocc.html**. Para evitar archivos numerados, usa **Guardar o reemplazar mi copia** y selecciona el HTML anterior en su carpeta; confirma el reemplazo cuando lo solicite el navegador. Esta opción depende de la compatibilidad del navegador. Una descarga normal no puede sobrescribir automáticamente tu archivo local.

La ruta `index_completo.html` se mantiene como copia idéntica de compatibilidad para que las versiones anteriores continúen detectando actualizaciones. Solo necesitas conservar un HTML local.

## Actualizar tu copia

1. Abre el catálogo y pulsa **Buscar actualizaciones**.
2. Si hay una versión nueva, BullDocc descarga el HTML y verifica su tamaño, huella SHA-256 y versión interna.
3. Pulsa **Descargar actualización** o **Guardar o reemplazar mi copia**, cuando el navegador permita elegir el archivo de destino.
4. Abre la nueva copia. Puedes conservar o reemplazar el HTML anterior.

El navegador pide intervención para guardar o reemplazar archivos; BullDocc no modifica silenciosamente el archivo abierto. La consulta requiere Internet y solo obtiene `version.json` y, si hay actualización, el HTML publicado en este repositorio. No envía los datos ni archivos de tus pruebas a GitHub.

## Herramientas QA integradas

Despliega **Herramientas QA · semilla, casuísticas y validación** dentro de cada generador.

- Activa la semilla y fija una fecha de referencia para repetir contenido con las mismas opciones, entrada y versión. El cruce con cartera conserva su lógica determinista según sus entradas; cambiar la semilla no altera su resultado. La repetición se refiere al contenido, no a los metadatos del ZIP.
- Consulta la ficha con descripción, salidas y opciones del generador.
- Genera y descarga el informe QA con versión, semilla, opciones y hallazgos. La revisión comprueba estructuras y relaciones disponibles sin bloquear ni corregir los errores deliberados. Los archivos sin perfil quedan fuera de la revisión; no equivale a certificación SUCC.
- Volver al catálogo conserva los formularios, resultados y archivos cargados durante la sesión. Recargar o cerrar el HTML descarta ese estado.

Todo queda incluido en el mismo `index_completo.html`; no requiere archivos adicionales ni servidor para generar y revisar.

## Contenido publicado

- `index_completo.html`: aplicación completa.
- `version.json`: versión publicada, URL y SHA-256 del HTML.
- Este documento de uso y publicación.

Se incluyen generadores AFP, IPS/FAPP, pagos, rebajas, MOVPER, MDF y retroalimentación. Cada herramienta conserva su contexto y sus propias casuísticas. La aceptación de los archivos requiere certificación en el ambiente QA correspondiente.

## Publicar una nueva versión

El mantenimiento se realiza en el proyecto local con los fuentes de los generadores. Después de editar y verificar los HTML afectados, ejecutar desde su raíz:

```sh
python3 auditoria/empaquetado/preparar_publicacion.py --version 1.2.1 --notas "Descripción del cambio"
```

La verificación de integridad exige registrar los cambios intencionales de los generadores en `auditoria/empaquetado/correcciones_aprobadas.json` del proyecto de fuentes.

El comando reconstruye y verifica el paquete, y prepara el HTML y el manifiesto en `publicacion/BullDocc/`. Revisa los archivos y publícalos juntos:

```sh
cd publicacion/BullDocc
git add index_completo.html version.json
git commit -m "Publicar BullDocc 1.2.1"
git push origin main
gh release create v1.2.1 index_completo.html version.json --title "BullDocc 1.2.1" --notes "Descripción del cambio"
```

Cada publicación requiere una versión mayor que la anterior en formato `mayor.menor.parche`. El botón no ofrece volver a versiones inferiores. No edites `version.json` a mano ni publiques un manifiesto que no corresponda al HTML.

Las bibliotecas de terceros conservan sus avisos de licencia dentro del HTML.

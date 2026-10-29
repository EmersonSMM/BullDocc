# BullDocc · Generadores QA

23 generadores de datos y archivos para pruebas QA, reunidos en un HTML autocontenido.

## Descargar y utilizar

Descarga **index_completo.html** desde [Releases](https://github.com/EmersonSMM/BullDocc/releases/latest) y ábrelo en tu navegador. Incluye estilos, imágenes, JSZip y PapaParse; la generación de archivos funciona localmente.

## Actualizar tu copia

1. Abre el catálogo y pulsa **Buscar actualizaciones**.
2. Si hay una versión nueva, BullDocc descarga el HTML y verifica su tamaño, huella SHA-256 y versión interna.
3. Pulsa **Descargar actualización** o **Guardar archivo actualizado**, cuando el navegador permita elegir el archivo de destino.
4. Abre la nueva copia. Puedes conservar o reemplazar el HTML anterior.

El navegador pide intervención para guardar o reemplazar archivos; BullDocc no modifica silenciosamente el archivo abierto. La consulta requiere Internet y solo obtiene `version.json` y, si hay actualización, el HTML publicado en este repositorio. No envía los datos ni archivos de tus pruebas a GitHub.

## Contenido publicado

- `index_completo.html`: aplicación completa.
- `version.json`: versión publicada, URL y SHA-256 del HTML.
- Este documento de uso y publicación.

Se incluyen generadores AFP, IPS/FAPP, pagos, rebajas, MOVPER, MDF y retroalimentación. Cada herramienta conserva su contexto y sus propias casuísticas. La aceptación de los archivos requiere certificación en el ambiente QA correspondiente.

## Publicar una nueva versión

El mantenimiento se realiza en el proyecto local con los fuentes de los generadores. Después de editar y verificar los HTML afectados, ejecutar desde su raíz:

```sh
python3 auditoria/empaquetado/preparar_publicacion.py --version 1.0.1 --notas "Descripción del cambio"
```

El comando reconstruye y verifica el paquete, y prepara el HTML y el manifiesto en `publicacion/BullDocc/`. Revisa los archivos y publícalos juntos:

```sh
cd publicacion/BullDocc
git add index_completo.html version.json
git commit -m "Publicar BullDocc 1.0.1"
git push origin main
gh release create v1.0.1 index_completo.html version.json --title "BullDocc 1.0.1" --notes "Descripción del cambio"
```

Cada publicación requiere una versión mayor que la anterior en formato `mayor.menor.parche`. El botón no ofrece volver a versiones inferiores. No edites `version.json` a mano ni publiques un manifiesto que no corresponda al HTML.

Las bibliotecas de terceros conservan sus avisos de licencia dentro del HTML.

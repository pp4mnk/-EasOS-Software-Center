# Easy Software Center

### Edición española · …by pp4mnk

**Descubre, instala y gestiona software en EasyOS desde una interfaz gráfica.**

Easy Software Center reúne un catálogo de paquetes nativos con buscador, una selección de aplicaciones populares, un gestor integrado de AppImages y accesos directos a las herramientas de software de EasyOS. Su objetivo es facilitar la búsqueda e instalación de programas, mostrando información sobre cada aplicación y solicitando confirmación antes de instalar.

Esta documentación corresponde a la versión del programa con interfaz en español.

## Funciones

- **Catálogo local completo de APT:** consulta los paquetes disponibles en los repositorios configurados.
- **38 aplicaciones destacadas:** descubre programas de navegación, ofimática, gráficos, multimedia, educación, desarrollo y otras categorías.
- **Buscador y filtros por categoría:** encuentra paquetes por nombre, descripción, identificador o categoría, con 40 resultados por página.
- **Instalación con doble clic y confirmación:** prepara la instalación de un paquete nativo, revisa las dependencias y los cambios propuestos y pulsa **Instalar**.
- **Actualización del índice de paquetes:** renueva la información de los repositorios sin realizar una actualización general de los programas.
- **Información de las aplicaciones:** consulta descripciones, páginas oficiales y foros identificados, con enlaces visibles que puedes copiar.
- **Gestión de AppImages:** descarga versiones seleccionadas desde GitHub, importa archivos locales, ejecuta, actualiza, elimina y restaura una versión anterior.
- **Accesos a los gestores de EasyOS:** abre PKGget, SFSget, Appi y Flapi cuando estén disponibles.
- **Gestión de archivos locales:** deriva los formatos admitidos al procedimiento correspondiente de EasyOS.
- **Interfaz en español:** los textos de la interfaz, la ayuda y la documentación están en español.

## Requisitos

- EasyOS 7.x; los metadatos del paquete están dirigidos a Excalibur.
- Python 3.8 o posterior.
- PyGObject (`python3-gi`) y GTK 3 (`gir1.2-gtk-3.0`, o los paquetes equivalentes de tu edición).
- APT y repositorios configurados para el catálogo nativo y la instalación directa de paquetes nativos.
- Privilegios de administrador para instalar paquetes nativos y actualizar el índice.
- Linux **x86_64** para el instalador integrado de AppImages.
- Conexión a Internet para las descargas, la actualización de repositorios y los enlaces externos.

No requiere dependencias instaladas mediante pip. PKGget, SFSget, Appi, Flapi y `petget` deben estar presentes para utilizar sus respectivas integraciones.

## Instalación

1. Descarga el paquete PET de la edición española desde el lugar de este repositorio donde se publique el paquete.
2. Cierra cualquier instancia abierta de Easy Software Center.
3. Haz doble clic en el archivo PET desde EasyOS y acepta la instalación.
4. Abre **Menú → Utilidades → Easy Software Center**. La ubicación exacta puede variar.
5. Guarda la sesión de EasyOS si el modo de funcionamiento que utilizas lo requiere para conservar los cambios después de reiniciar.

También puedes abrir el programa desde una terminal:

```sh
easy-software-center
```

Si aparece un aviso sobre dependencias, instala Python 3, PyGObject y GTK 3 mediante PKGget y vuelve a abrir el programa.

## Uso del catálogo

Selecciona una fuente:

| Fuente | Contenido |
| --- | --- |
| **Destacadas** | 38 aplicaciones seleccionadas, con enlaces útiles e indicación de las opciones de instalación disponibles. |
| **Paquetes nativos** | El índice local completo de APT correspondiente a los repositorios configurados. |
| **Instaladas · AppImages ESC** | AppImages instaladas o importadas mediante este centro de software. |

Escribe un término de búsqueda, elige una categoría y consulta los resultados. Pulsa una entrada para ver sus detalles y las acciones disponibles.

**Recargar catálogo** vuelve a leer el índice local existente de APT. **Actualizar índice** actualiza la información desde los repositorios configurados y después recarga el catálogo. Actualizar el índice no instala ni actualiza aplicaciones.

### Instalación de paquetes nativos

Haz doble clic en una entrada nativa o selecciónala y pulsa **Instalar paquete**. Primero, el programa solicita a APT una simulación de la instalación. Revisa las dependencias y los cambios propuestos y pulsa **Instalar** para continuar.

La instalación utiliza APT con `--no-remove`, que bloquea los planes que requieren eliminar paquetes, y conserva los archivos de configuración existentes cuando dpkg normalmente preguntaría si deben sustituirse. El plan puede incluir dependencias y actualizaciones necesarias para la instalación seleccionada.

Utiliza **Gestionar en PKGget** para abrir el gestor de paquetes por separado. El nombre del paquete seleccionado se copia al portapapeles para que puedas pegarlo en su buscador.

### Gestión de AppImages

En las aplicaciones destacadas que ofrecen esta opción, pulsa **Descargar AppImage de GitHub**. El programa busca una AppImage adecuada en la última versión publicada del proyecto en GitHub y muestra la versión, el archivo, el tamaño y el origen de la descarga antes de instalar.

Utiliza **Archivo local…** para importar una AppImage x86_64 que ya tengas. Las AppImages instaladas aparecen en **Instaladas · AppImages ESC**, desde donde puedes ejecutarlas o eliminarlas. Las entradas vinculadas a GitHub también permiten buscar actualizaciones. Al sustituir una AppImage instalada, se conservan el ejecutable anterior y sus metadatos para poder utilizar **Restaurar AppImage anterior**.

El instalador valida la cabecera AppImage y la arquitectura x86_64, calcula SHA-256 y lo compara con el valor publicado cuando GitHub proporciona un resumen SHA-256. Calcular una suma de comprobación por sí solo no verifica al editor. Las aplicaciones no se ejecutan automáticamente durante la instalación.

Restaurar una AppImage anterior recupera su ejecutable y los metadatos de instalación; no restaura los documentos ni la configuración de la aplicación.

### Apertura de archivos locales

| Tipo de archivo | Comportamiento |
| --- | --- |
| `.AppImage` | Importa una AppImage x86_64 admitida al gestor integrado, previa confirmación. |
| `.pet`, `.deb`, `.rpm`, `.tar.xz` | Envía el archivo seleccionado a `petget`, previa confirmación. La compatibilidad real depende de EasyOS y del paquete. |
| `.sfs` | Muestra instrucciones para seleccionar el archivo en Easy BootManager, dentro del menú Sistema de archivos. |
| `.flatpakref`, `.flatpak` | Abre Flapi e indica que debes importar el archivo desde ese gestor. |

La barra superior también ofrece acceso directo a **PKGget**, **SFSget**, **Appi** y **Flapi**. Sus catálogos y operaciones de instalación se gestionan desde esas herramientas.

## Aplicaciones destacadas

Las 38 entradas destacadas incluyen Firefox, Chromium, Thunderbird, VLC, GIMP, LibreOffice, Blender, Scribus, OBS Studio, mpv, Audacious, FileZilla, Transmission, Geany, Git, GParted, Syncthing, Calibre, Stellarium, GCompris, Tux Paint, Scratch, SuperTuxKart, Battle for Wesnoth, BleachBit, Remmina, KeePassXC, Krita, Shotcut, Kdenlive, FreeCAD, Inkscape, Obsidian, Joplin, LocalSend, QOwnNotes, balenaEtcher y Audacity.

Las entradas destacadas ayudan a descubrir programas. Su presencia no garantiza que exista un paquete nativo disponible o una AppImage de GitHub compatible.

## Archivos y datos

| Ubicación | Función |
| --- | --- |
| `/usr/local/bin/easy-software-center` | Lanzador y comprobación de dependencias. |
| `/usr/local/lib/easy-software-center/center.py` | Aplicación en Python. |
| `/usr/share/applications/easy-software-center.desktop` | Entrada en el menú del sistema. |
| `/usr/share/doc/easy-software-center/README.txt` | Documentación incluida y texto de la licencia MIT. |
| `~/.local/share/easy-software-center/` | AppImages gestionadas, metadatos, caché de iconos y registros. |
| `~/.local/share/applications/esc-*.desktop` | Lanzadores de menú de las AppImages gestionadas. |

Las ediciones española e inglesa 0.3 utilizan las mismas ubicaciones de almacenamiento de AppImages. Si el instalador reconoce una entrada antigua del menú de usuario creada por la edición distribuida como script, guarda una copia con el sufijo `.before-pet` antes de eliminar esa entrada duplicada.

## Limitaciones y solución de problemas

- **El tamaño del catálogo varía:** los resultados dependen de los repositorios configurados y de lo actualizado que esté el índice local. También incluye bibliotecas, documentación y herramientas de terminal, por lo que no todas las entradas abren una aplicación gráfica.
- **APT no está disponible:** utiliza PKGget en tu edición. Si no se cargan entradas nativas, el programa muestra el catálogo de aplicaciones destacadas.
- **No hay una AppImage adecuada en GitHub:** es posible que la última versión publicada no incluya ninguna. Consulta la página oficial de la aplicación para encontrar otras descargas.
- **Una AppImage no arranca:** revisa su archivo `launch.log` dentro de su carpeta en `~/.local/share/easy-software-center/`. Puede necesitar FUSE o dependencias adicionales. El programa no desactiva automáticamente el aislamiento de seguridad de las aplicaciones.
- **Falla una instalación nativa:** consulta el archivo `apt-<package>.log` correspondiente en la carpeta de datos del centro de software.
- **No se abre una página web:** copia la dirección mostrada y ábrela manualmente. Los errores al iniciar el navegador se registran en `browser.log`, dentro de la misma carpeta de datos.
- **No funciona el acceso a un gestor:** esa herramienta puede no estar incluida en tu edición de EasyOS.

Los paquetes externos y las AppImages no están certificados para todas las versiones de EasyOS. Esta edición española está pensada para usuarios de EasyOS de habla hispana; no se garantiza su compatibilidad con otras distribuciones Linux ni con otras arquitecturas de CPU. Las páginas web, los gestores y las aplicaciones de terceros mantienen sus propios ajustes de idioma.

La documentación incluida en el paquete indica que se realizaron comprobaciones de sintaxis, integridad, traducción y lógica principal, pero no una instalación ni pruebas visuales en una sesión real de EasyOS dentro del entorno de creación.

## Desinstalación

Desinstala **Easy Software Center** mediante PKGget. Las AppImages y los datos del usuario se conservan.

Para eliminar una AppImage gestionada por el centro, selecciónala y pulsa **Eliminar AppImage**. Se eliminan su ejecutable gestionado, la versión anterior conservada, los metadatos de instalación asociados y el lanzador del menú. Los documentos y las preferencias de la aplicación almacenados en otras ubicaciones se conservan.

## Comunicación de problemas

Al informar de un problema en la sección de incidencias de este repositorio, incluye tu versión de EasyOS, la arquitectura de CPU, la aplicación o el paquete afectado, los pasos para reproducirlo y el mensaje de error o fragmento relevante del registro. Elimina la información personal antes de publicar registros.

## Licencia

Easy Software Center se distribuye bajo la **licencia MIT**.

Copyright © 2026 pp4mnk. El texto completo de la licencia se incluye en el archivo `README.txt` del paquete PET. Las aplicaciones y los logotipos de terceros mantienen sus respectivas licencias.

---

**Easy Software Center  · …by pp4mnk**

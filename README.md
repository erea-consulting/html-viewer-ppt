# HTML Viewer (EREA) · complemento de PowerPoint

Complemento de PowerPoint de EREA Consulting Group que muestra un gráfico HTML interactivo dentro de una lámina. El HTML se guarda dentro del propio `.pptx`, así que viaja con el archivo.

- **Visor publicado:** https://erea-consulting.github.io/html-viewer-ppt/viewer.html
- **Página de instalación:** https://erea-consulting.github.io/html-viewer-ppt/
- **Manifest vigente:** `html-viewer-erea-web.xml`, versión 1.1.0.0

## Instalación

### Mac

Pega esto en Terminal:

```bash
mkdir -p ~/Library/Containers/com.microsoft.Powerpoint/Data/Documents/wef
curl -fsSL https://erea-consulting.github.io/html-viewer-ppt/html-viewer-erea-web.xml \
  -o ~/Library/Containers/com.microsoft.Powerpoint/Data/Documents/wef/html-viewer-erea-web.xml
```

Cierra PowerPoint por completo (Cmd+Q) y vuelve a abrirlo. El complemento aparece en **Insertar → Complementos → Mis complementos → HTML Viewer (EREA)**.

### PowerPoint web

Descarga [`html-viewer-erea-web.xml`](https://erea-consulting.github.io/html-viewer-ppt/html-viewer-erea-web.xml) y súbelo en **Insertar → Complementos → Cargar mi complemento**.

### Windows (escritorio)

1. Descarga `html-viewer-erea-web.xml` en una carpeta compartida de red.
2. En PowerPoint: **Archivo → Opciones → Centro de confianza → Configuración del Centro de confianza → Catálogos de complementos de confianza**. Agrega la ruta de la carpeta y marca «Mostrar en el menú».
3. Reinicia PowerPoint. El complemento aparece en **Insertar → Complementos → Mis complementos → Carpeta compartida**.

### Toda la firma

El administrador de Microsoft 365 puede desplegarlo para todos desde **Configuración → Aplicaciones integradas → Cargar aplicación personalizada**, con el mismo manifest.

### Si ya tenías una versión anterior

Reemplaza el archivo de la carpeta `wef` por el nuevo, con el mismo nombre, y reabre PowerPoint. Los decks ya hechos no cambian.

## Uso

1. Con la lámina activa, abre el complemento.
2. Arrastra el archivo `.html` o `.svg` al panel, o usa **Cargar HTML…** o **Pegar código**.
3. Ajusta el zoom. En modo presentación la barra desaparece.
4. Guarda el deck (Cmd+S o Ctrl+S): el HTML queda dentro del `.pptx`.

A tener en cuenta:

- Un gráfico ya insertado no se actualiza solo. Si el archivo cambió, vuelve a cargarlo.
- Al duplicar una lámina con gráfico, vuelve a cargar el HTML en la copia.
- El visor avisa a partir de 1.5 MB y suele fallar cerca de 4 MB.
- Quien abra el deck sin el complemento instalado ve un marcador vacío. Para enviar o exportar a PDF, usa el gráfico nativo de PowerPoint.

## Seguridad y privacidad

- El visor es una página estática. El HTML que cargas se guarda en el `.pptx` y no se envía a ningún servidor.
- El permiso `ReadWriteDocument` es el mínimo que exige Office para que un complemento de contenido escriba dentro del archivo. No lee otros documentos.
- El HTML se muestra en un `iframe` con `sandbox`. Carga solo archivos de origen conocido.

## Archivos

| Archivo | Qué es |
|---|---|
| `viewer.html` | El visor que PowerPoint carga por HTTPS |
| `html-viewer-erea-web.xml` | Manifest del complemento (el que se instala) |
| `manifest-pages.xml` | Copia idéntica del manifest, con el nombre anterior |
| `index.html` | Página de instalación |
| `icon-32.png`, `icon-64.png`, `icon-80.png` | Iconos |

## Mantenimiento

- Los cambios en `main` se publican solos en GitHub Pages en uno o dos minutos.
- Si cambia la dirección del visor, regenera el manifest con el **mismo Id** (`78cd38eb-fd45-4d43-8d64-4a3c0aa80232`) y sube la versión. PowerPoint lo trata como el mismo complemento.
- Los dos archivos de manifest deben quedar idénticos.

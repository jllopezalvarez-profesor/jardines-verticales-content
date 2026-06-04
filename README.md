# Jardines Verticales - Contenido

Este repositorio contiene la información detallada y los recursos multimedia (imágenes) de los diferentes jardines verticales que forman parte del proyecto. Actúa como un sistema de gestión de contenidos (CMS) basado en ficheros para las aplicaciones que consumen estos datos.

## Estructura de Directorios y Ficheros

La organización del repositorio sigue una estructura jerárquica por jardín:

```text
/
├── gardens/
│   ├── index.json             # Índice global de todos los jardines
│   └── <garden-id>/           # Carpeta específica por cada jardín (ej. ies-clara-del-rey)
│       ├── index.json         # Datos específicos y configuración del jardín
│       ├── logo.jpg           # Imagen del logo del centro o jardín
│       ├── banner.jpg         # Imagen de cabecera para la ficha del jardín
│       └── img/               # Galería de imágenes del jardín
│           ├── 1.jpg
│           └── ...
```

## Estructura de los Ficheros JSON

### 1. Índice Global (`gardens/index.json`)

Este fichero es el punto de entrada para descubrir qué jardines están disponibles en el sistema.

- `gardens`: (array) Lista de objetos que representan cada jardín.
    - `id`: (string) Identificador único del jardín (coincide con el nombre de su carpeta). La aplicación cliente debe construir la ruta al detalle del jardín basándose en este ID (ej: `gardens/<id>/index.json`).

### 2. Índice de Jardín (`gardens/<garden-id>/index.json`)

Contiene toda la información detallada, rutas de imágenes y enlaces de un jardín específico.

- `id`: (string) Identificador único del jardín.
- `name`: (string) Nombre descriptivo del jardín o centro educativo.
- `updatedAt`: (string) Fecha de la última actualización de los datos de este jardín en formato ISO 8601.
- `logo`: (string) Ruta relativa al fichero de imagen del logo.
- `banner`: (string) Ruta relativa al fichero de imagen del banner.
- `metricsUrl`: (string) URL del punto de conexión (endpoint) para obtener las métricas en tiempo real (humedad, temperatura, etc.).
- `images`: (array de strings) Lista de rutas relativas a las imágenes en la carpeta `img/`.
- `links`: (objeto) Colección de enlaces externos relacionados.
    - `web`: (string, opcional) URL del sitio web oficial.
    - `instagram`: (string, opcional) URL del perfil de Instagram.

## Convenciones de Contenido

- Todas las rutas en los ficheros JSON deben ser relativas a la ubicación del propio fichero JSON.
- Se recomienda que las imágenes tengan un formato optimizado (JPG o WebP) para mejorar el rendimiento de carga en las aplicaciones finales.
- El identificador del jardín (`id`) debe ser en minúsculas y usar guiones para separar palabras (kebab-case).

## Cómo añadir un nuevo jardín

Para añadir un nuevo jardín al repositorio, sigue estos pasos:

1. **Copiar la plantilla**: Copia la carpeta `gardens/garden-sample` y cámbiale el nombre al ID de tu nuevo jardín (ej: `gardens/mi-jardin-nuevo`).
2. **Preparar recursos**:
   - Sustituye `logo.jpg` y `banner.jpg` por las imágenes de tu centro.
   - Sube las imágenes de la galería a la carpeta `img/`.
3. **Configurar datos**: Edita el fichero `index.json` dentro de tu nueva carpeta:
   - Cambia el `id` para que coincida con el nombre de la carpeta.
   - Actualiza el `name`, `metricsUrl`, la lista de imágenes y los enlaces.
   - Actualiza `updatedAt` con la fecha actual.
4. **Registrar en el índice**: Añade el nuevo ID al fichero global `gardens/index.json`:
   ```json
   {
     "id": "mi-jardin-nuevo"
   }
   ```

# Acciones Correctivas y de Mejora — Codere (SG-SST)

Tablero web para la gestión de hallazgos, no conformidades y oportunidades de mejora del Sistema de Gestión de Seguridad y Salud en el Trabajo. Incluye el ciclo de vida por estados, cálculo automático de plazos según criticidad, asistente de análisis de causa (Cinco porqués e Ishikawa Seis M) y la normativa colombiana aplicable en cada hallazgo.

Precargado con **91 hallazgos reales** de 7 sedes (Fantasía Royal, Mundo Fortuna y Crown Casinos), extraídos de las inspecciones locativas de septiembre de 2026.

## Contenido del repositorio

- `index.html` — la aplicación (interfaz, lógica y estilos en un solo archivo).
- `datos.js` — los hallazgos precargados (editable como texto).
- `.nojekyll` — evita que GitHub Pages procese el sitio con Jekyll.

No requiere servidor, dependencias ni compilación: es HTML, CSS y JavaScript estáticos.

## Publicar en GitHub Pages

1. Crea un repositorio nuevo en GitHub (por ejemplo `acciones-correctivas-codere`).
2. Sube estos tres archivos a la raíz del repositorio (arrástralos en **Add file → Upload files**, o por línea de comandos, ver abajo).
3. En el repositorio ve a **Settings → Pages**.
4. En **Source** elige la rama `main` y la carpeta `/ (root)`. Guarda.
5. En uno o dos minutos el sitio queda publicado en:
   `https://<tu-usuario>.github.io/<nombre-del-repo>/`

### Por línea de comandos

```bash
git init
git add index.html datos.js .nojekyll README.md
git commit -m "Tablero de acciones correctivas Codere (SG-SST)"
git branch -M main
git remote add origin https://github.com/<tu-usuario>/<nombre-del-repo>.git
git push -u origin main
```

Luego activa Pages como en los pasos 3–5.

## Uso

- **Tablero**: hallazgos por estado (Registrado → En análisis → En ejecución → Evaluación de eficacia → Cerrado), con indicadores de resumen, distribución por criticidad y semáforo de plazos. Filtra por sede y criticidad. Los botones de cada tarjeta avanzan el estado y validan los campos obligatorios de cada transición.
- **Registrar hallazgo**: formulario con cálculo automático de fechas límite.
- **Análisis de causa**: asistente paso a paso (Cinco porqués / Diagrama Seis M).

## Editar los datos

Los hallazgos están en `datos.js` como un arreglo `DATOS_HALLAZGOS`. Cada elemento tiene:

```js
{
  consecutivo, sede, unidad, clasificacion, origen, criticidad,
  descripcion, correccion, responsableArea, norma, fechaRegistroISO
}
```

Valores de `criticidad`: `ALTA`, `MEDIA`, `BAJA` (definen el plazo: 30, 45 y 60 días calendario, más 10 días hábiles de análisis).

## Nota sobre la marca

La paleta (verde corporativo, morado para casino y grises) está inspirada en la identidad visual de Codere para uso interno del sistema de gestión. No reproduce el logotipo oficial.

## Alcance

Interfaz de demostración: el estado no se persiste al recargar la página. La lógica de dominio lista para integrarse a una base de datos (esquema Prisma, servicios y componentes React) se entrega por separado.

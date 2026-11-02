# SCRATCHXR LAB

Plataforma educativa web para aprender programación por bloques creando, practicando y explorando modelos 3D, realidad aumentada (RA) y realidad virtual (RV). Está diseñada para estudiantes de **3.º a 11.º grado**. Funciona como una aplicación estática: no necesita servidor propio ni instalación.

## Qué incluye

### Para estudiantes

- **Misiones progresivas** organizadas por grado, con explicaciones, actividades y reflexión.
- **Teoría** de bloques, algoritmos, ejemplos y glosario adaptados al nivel.
- **Retos**: quizzes, ordenar código y encontrar errores, con retroalimentación y progreso.
- **Laboratorio XR**: visor 3D, acceso a RA cuando el dispositivo lo admite y escena RV con A-Frame.
- **Logros y gamificación**: XP, insignias, racha diaria, reto diario, desafío de ascenso y tabla de líderes local.
- **Lectura en voz alta** del navegador y preferencias de accesibilidad.
- Perfiles para los grados **3.º a 11.º**.

### Para docentes

- Panel con acceso mediante PIN, vista previa por grado, edición de lecciones y quizzes.
- Seguimiento de estudiantes de este dispositivo, exportación CSV y portabilidad de contenido JSON.
- Ajustes para cambiar el PIN, el modelo 3D predeterminado y la visibilidad de opciones de gamificación.

## Archivos del repositorio

La publicación desde la raíz (`/ (root)`) debe tener esta estructura:

```text
scratchxr-lab/
├── index.html
├── README.md
├── .nojekyll                 # archivo vacío
└── assets/
    └── models/
        ├── README.md         # instrucciones para modelos propios
        └── mi-modelo.glb     # ejemplo: añade aquí tu archivo GLB
```

`mi-modelo.glb` es un ejemplo de nombre, no viene incluido. Puedes reemplazarlo por cualquier archivo `.glb` tuyo y usar su nombre exacto en Ajustes. El nombre distingue mayúsculas y minúsculas.

El HTML incluye su CSS, JavaScript y favicon SVG. Las dependencias externas se solicitan por HTTPS con versiones fijadas: **model-viewer 4.0.0** y **A-Frame 1.7.0**. A-Frame se carga al entrar al Laboratorio XR. No se incluye una dependencia de MediaPipe en esta versión. El modelo astronauta inicial se obtiene de un sitio externo; puedes cambiarlo por uno del mismo repositorio.

## Acceso docente

En la pantalla inicial, selecciona **Entrar como docente** e introduce el PIN inicial **1234**. Para cambiarlo, abre **Ajustes** en el panel docente, escribe el PIN nuevo y guárdalo. El PIN es una barrera para evitar entradas accidentales, no un sistema de seguridad: al ser una aplicación sin servidor, no debe usarse para proteger información privada. El rol docente no permanece activo al recargar la página.

## Requisitos de 3D, RA, RV y cámara

- **3D:** navegador moderno con WebGL y conexión a Internet para descargar model-viewer y el modelo inicial. Un archivo del repositorio puede sustituir al modelo remoto.
- **RA:** el sitio debe estar publicado mediante **HTTPS**. Se necesita un dispositivo compatible. En Android suele requerirse ARCore y Scene Viewer; en iPhone o iPad se usa Quick Look con Safari. La aplicación comprueba la capacidad de `model-viewer`; si no está disponible, conserva el modo 3D y no simula RA.
- **RV:** se necesita un navegador y dispositivo compatibles con WebXR; para una experiencia inmersiva, un visor de RV compatible. Si el navegador no admite RV, aún puedes usar 3D.
- **Cámara:** la cámara del sistema puede ser necesaria al iniciar una experiencia de RA. Acepta el permiso del navegador cuando el sistema lo solicite. Para el uso de un modelo local no se necesita permiso de cámara.
- El acceso real a RA/RV depende del dispositivo, navegador, permisos y compatibilidad de sus servicios nativos.

## Datos y limitaciones

Los perfiles, XP, resultados y ajustes se guardan en el almacenamiento local del navegador de cada dispositivo. **No se sincronizan entre dispositivos ni se envían a un servidor.** Borrar los datos del navegador o cambiar de dispositivo puede hacer que se pierdan o no aparezcan los perfiles. Usa las opciones de exportación del panel docente para guardar una copia del contenido o los resultados que necesites transferir. El PIN docente también se almacena localmente y no sustituye una autenticación de servidor.

La voz usa Web Speech API. Las voces disponibles dependen del navegador y del sistema operativo. Algunas funciones de RA y RV requieren conexión y servicios compatibles del dispositivo.

## Publicar en GitHub Pages desde la web de GitHub

1. Inicia sesión en [GitHub](https://github.com/). En la esquina superior derecha, pulsa **+** y elige **New repository**.
2. Escribe un nombre, por ejemplo `scratchxr-lab`. Para empezar con la configuración más sencilla, crea un repositorio **Public**. Si eliges uno privado, la disponibilidad de Pages puede depender del plan o de las políticas de tu organización.
3. Deja seleccionada la rama `main`. Puedes marcar **Add a README file** o no hacerlo; si ya se creó otro README, luego podrás reemplazarlo.
4. Pulsa **Create repository**.
5. En la pestaña **Code**, elige **Add file > Upload files**. Sube `index.html`, `README.md` y `.nojekyll` desde la carpeta de tu computadora. Si aparece un README inicial, puedes reemplazarlo con el de este proyecto.
6. Crea el archivo `assets/models/README.md` desde **Add file > Create new file** y escribe `assets/models/README.md` como nombre. Pega el contenido del archivo que acompaña a este repositorio y pulsa **Commit changes**. Esto crea la carpeta para los modelos.
7. Si tienes un modelo, abre `assets/models/` y usa **Add file > Upload files** para subir, por ejemplo, `mi-modelo.glb`. Confirma que el nombre coincide exactamente con el que vas a escribir en Ajustes.
8. Confirma que los archivos están en la raíz del repositorio, no dentro de otra carpeta contenedora: `index.html`, `README.md`, `.nojekyll` y `assets/` deben aparecer al abrir la pestaña **Code**.
9. En el repositorio, abre **Settings > Pages**. En **Build and deployment**, selecciona **Deploy from a branch**. En **Branch**, elige `main`; en la carpeta, elige **/(root)**; luego pulsa **Save**.
10. Espera a que termine la implementación. Puedes revisar su estado en **Actions** o volver a **Settings > Pages**. Para un repositorio llamado `scratchxr-lab`, la dirección normalmente tendrá la forma `https://TU-USUARIO.github.io/scratchxr-lab/`. Sustituye `TU-USUARIO` por tu nombre de usuario. La primera publicación puede tardar unos minutos.

GitHub mantiene una [guía oficial de inicio de Pages](https://docs.github.com/en/pages/quickstart) y la [configuración de publicación desde una rama](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site). Los sitios Pages publicados son accesibles por Internet; no subas datos privados de estudiantes al repositorio.

## Actualizar el sitio

1. Abre el repositorio y selecciona el archivo que quieres actualizar.
2. Para editar texto, pulsa el icono del lápiz, cambia el contenido y pulsa **Commit changes**. Para reemplazar `index.html` o un modelo, usa **Add file > Upload files** y sube la versión nueva en la misma ruta.
3. Asegúrate de guardar los cambios en `main`. GitHub Pages volverá a publicar el sitio automáticamente.
4. Espera a que la ejecución de Pages en **Actions** termine y recarga el sitio. Si el navegador muestra la versión anterior, prueba una recarga forzada.

## Usar un GLB alojado en este mismo repositorio

1. Sube el archivo a `assets/models/`, por ejemplo `assets/models/robot-aula.glb`.
2. En el sitio publicado, entra como docente y abre **Ajustes**.
3. En el campo del modelo predeterminado, escribe la ruta relativa exacta: `assets/models/robot-aula.glb`. No pongas una barra inicial y respeta las mayúsculas del nombre.
4. Pulsa **Guardar URL**. También puedes usar la opción para cargar un modelo en el Laboratorio XR con esa misma ruta.
5. Comprueba que el archivo está publicado abriendo una dirección como `https://TU-USUARIO.github.io/scratchxr-lab/assets/models/robot-aula.glb`. Debe descargarse o mostrarse sin una página 404.

La ruta relativa se resuelve desde la ubicación del sitio e incluye automáticamente el subdirectorio del repositorio. Al cargarlo desde el mismo sitio, el modelo usa el mismo origen y normalmente evita los bloqueos CORS de un servidor externo. Si usas una URL alojada fuera de GitHub, ese servidor debe permitir solicitudes desde el sitio mediante sus encabezados CORS.

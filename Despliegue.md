# Despliegue de poke-dex-lab en Azure

## Descripción
Se realizó el despliegue de la aplicación **poke-dex-lab** en la plataforma de Azure, asegurando que todos los servicios necesarios estuvieran correctamente configurados y operativos.

Primero, se descargó el archivo ZIP que estaba en el enlace de GitHub. Una vez descargado, se procedió con la instalación de **Node.js** y **Angular** de forma local.

Después de instalar, se procedio a ejecutar la aplicación de forma local ejecutando los comandos `npm install` y `npm start`, la cual, una vez iniciada, se validó en el host `http://localhost:4200/`.

Una vez confirmada que la pagina web servia, se realizo el despliegue con el comando `npm run build`, el cual creó una carpeta llamada **dist** con una subcarpeta llamada **pokedex-angular**. De esta subcarpeta, se comprimieron todos sus archivos a una carpeta llamada **pokedex-angular.zip**.

Una vez teniendo comprimido el archivo, se procedio a ingresar a la App Service creada en Azure. Nos dirigimos a **Herramientas de desarrollo**, **Herramientas avanzadas**, y después **Ir**. Una vez dentro, se dio clic en **Debug Console** y luego en **CMD**.

Una vez dentro, se seleccionó **site**, luego **wwwroot**, y el archivo comprimido se arrastró hasta el servidor creado, donde el mismo se descomprime.

Para crear los parámetros de seguridad, se creó un archivo **web.config** donde se establecieron los siguientes parámetros con ayuda de la inteligencia artificial y los prompts creados:

# Explicación del archivo web.config

## Descripción General
Un archivo `web.config` es un documento XML que configura un servidor web IIS (Internet Information Services). Este archivo en particular establece diversas configuraciones de seguridad y comportamiento para una aplicación web.

## Componentes Principales

### 1. Redirección HTTPS 🔒
La configuración implementa una redirección automática de HTTP a HTTPS:

- **Propósito**: Garantizar conexiones seguras
- **Tipo**: Redirección permanente (301)
- **Alcance**: Todas las URLs del sitio

### 2. Encabezados de Seguridad 🛡️
| Encabezado                     | Propósito                        | Configuración                   |
|---------------------------------|----------------------------------|---------------------------------|
| Strict-Transport-Security       | Forzar HTTPS                    | max-age=31536000               |
| Content-Security-Policy         | Controlar fuentes de recursos    | default-src 'self'             |
| X-Frame-Options                 | Prevenir clickjacking            | DENY                            |
| X-Content-Type-Options          | Prevenir MIME-sniffing           | nosniff                         |
| Referrer-Policy                 | Controlar info de referente      | no-referrer-when-downgrade     |
| Permissions-Policy              | Gestionar permisos               | geolocation=(self), microphone=() |

### 3. Configuración SPA 📱
Para aplicaciones de una sola página:

- ✅ Soporte para archivos JSON
- ✅ Manejo de rutas personalizado
- ✅ Configuración de archivos estáticos

### 4. Gestion de Errores 
- **404** → Redireccion a pagina principal

## Implementacion

1. Coloque el archivo en la raiz del proyecto.
2. Verifique la configuracion del servidor IIS.
3. Pruebe todas las redirecciones y encabezados.

## Consideraciones Importantes

**Nota**: Revise y ajuste los encabezados de seguridad según sus necesidades específicas.

## Checklist de Implementacion
- Verificar compatibilidad con IIS
- Probar redirecciones HTTPS
- Validar funcionamiento de SPA
- Comprobar encabezados de seguridad

Para más informacion, consulte la documentacion oficial de Microsoft IIS.

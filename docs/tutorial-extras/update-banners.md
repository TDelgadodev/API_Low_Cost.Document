---
sidebar_position: 1
---

# Actualización de Banners

El sistema incluye funcionalidades para gestionar banners, tanto horizontales como estáticos. A continuación, se describen las API y sus respectivas operaciones.

## API de Banners Horizontales

### Cargar Imágenes de Banners Horizontales

- **Descripción:** Esta API permite cargar exactamente tres imágenes de banners horizontales. Las imágenes se almacenan en el servidor y se devuelve una lista de rutas de acceso a las imágenes cargadas.

- **Ruta:** `/api/upload/upload-images`
- **Método:** POST
- **Cuerpo de la solicitud:** Debe contener tres imágenes.
- **Respuesta exitosa (200 OK):** Devuelve una lista de rutas de acceso a las imágenes cargadas.

### Eliminar Imágenes de Banners Horizontales

- **Descripción:** Esta API elimina todas las imágenes de banners horizontales existentes en el servidor.

- **Ruta:** `/api/upload/delete-images`
- **Método:** DELETE
- **Respuesta exitosa (200 OK):** Devuelve un mensaje indicando que las imágenes se eliminaron con éxito.

### Obtener Banners Horizontales

- **Descripción:** Esta API proporciona una lista de rutas de acceso a las imágenes de banners horizontales almacenadas en el servidor.

- **Ruta:** `/api/upload/horizontal-banners`
- **Método:** GET
- **Respuesta exitosa (200 OK):** Devuelve una lista de rutas de acceso a las imágenes de banners horizontales.

## API de Banners Estáticos

### Cargar Imágenes de Banners Estáticos

- **Descripción:** Esta API permite cargar exactamente tres imágenes de banners estáticos. Las imágenes se almacenan en el servidor y se devuelve una lista de rutas de acceso a las imágenes cargadas.

- **Ruta:** `/api/upload/upload-banners-static`
- **Método:** POST
- **Cuerpo de la solicitud:** Debe contener tres imágenes.
- **Respuesta exitosa (200 OK):** Devuelve una lista de rutas de acceso a las imágenes cargadas.

### Eliminar Imágenes de Banners Estáticos

- **Descripción:** Esta API elimina todas las imágenes de banners estáticos existentes en el servidor.

- **Ruta:** `/api/upload/delete-static-images`
- **Método:** DELETE
- **Respuesta exitosa (200 OK):** Devuelve un mensaje indicando que las imágenes se eliminaron con éxito.

### Obtener Banners Estáticos

- **Descripción:** Esta API proporciona una lista de rutas de acceso a las imágenes de banners estáticos almacenadas en el servidor.

- **Ruta:** `/api/upload/get-static-banners`
- **Método:** GET
- **Respuesta exitosa (200 OK):** Devuelve una lista de rutas de acceso a las imágenes de banners estáticos.

## Consideraciones Importantes

- Al cargar imágenes de banners, asegúrate de que el cuerpo de la solicitud contenga exactamente tres imágenes.
- La eliminación de imágenes es irreversible, y todas las imágenes existentes se eliminarán por completo.
- Las rutas de acceso a las imágenes se proporcionan en la respuesta de cada API para su posterior uso.

Estas funcionalidades de actualización de banners son útiles para administrar y personalizar los banners utilizados en tu aplicación. Asegúrate de proporcionar una interfaz de usuario fácil de usar para que los administradores de la aplicación puedan cargar y gestionar imágenes de banners según sea necesario.


---
sidebar_position: 4
---

# API de Administración

Esta API ofrece endpoints para administrar usuarios y productos en el sistema. A continuación, se describen los endpoints disponibles:

## Usuarios

### Obtener la lista de usuarios

- **Descripción:** Este endpoint permite obtener la lista de todos los usuarios registrados en el sistema.
- **Ruta:** `/api/admin/users`
- **Método:** GET
- **Respuesta exitosa (200 OK):** Devuelve la lista de usuarios con detalles como nombre, apellido, correo electrónico, dirección, etc.
- **Posibles respuestas de error:**
  - 500 Internal Server Error: Si ocurre un error inesperado al obtener la lista de usuarios.

## Productos

### Obtener la lista de productos

- **Descripción:** Este endpoint permite obtener la lista de todos los productos disponibles en el sistema.
- **Ruta:** `/api/admin/products`
- **Método:** GET
- **Respuesta exitosa (200 OK):** Devuelve la lista de productos con detalles como nombre, precio, descripción, categoría, marca, etc.
- **Posibles respuestas de error:**
  - 500 Internal Server Error: Si ocurre un error inesperado al obtener la lista de productos.

### Crear un nuevo producto

- **Descripción:** Este endpoint permite crear un nuevo producto en el sistema.
- **Ruta:** `/api/admin/create`
- **Método:** POST
- **Cuerpo de la solicitud:** Debe incluir detalles del producto, como título, precio, descripción, marca, categoría, stock, oferta, visibilidad y archivos de imagen.
- **Respuesta exitosa (200 OK):** Devuelve el producto creado con detalles y URL.
- **Posibles respuestas de error:**
  - 500 Internal Server Error: Si ocurre un error inesperado al crear el producto.

### Eliminar un producto

- **Descripción:** Este endpoint permite eliminar un producto específico según su ID.
- **Ruta:** `/api/admin/:id`
- **Método:** DELETE
- **Parámetros de consulta:** ID del producto a eliminar.
- **Respuesta exitosa (200 OK):** Indica que el producto se eliminó con éxito.
- **Posibles respuestas de error:**
  - 500 Internal Server Error: Si ocurre un error inesperado al eliminar el producto.

### Editar un producto

- **Descripción:** Este endpoint permite actualizar un producto existente en el sistema.
- **Ruta:** `/api/admin/edit/:id`
- **Método:** PUT
- **Parámetros de consulta:** ID del producto a editar.
- **Cuerpo de la solicitud:** Debe incluir detalles actualizados del producto.
- **Respuesta exitosa (200 OK):** Indica que el producto se actualizó con éxito.
- **Posibles respuestas de error:**
  - 500 Internal Server Error: Si ocurre un error inesperado al editar el producto.

### Editar Precios de Productos

- **Descripción:** Este endpoint permite editar los precios de los productos dentro de un rango específico o de manera individual. Puedes elegir si deseas actualizar el precio de manera absoluta o como un porcentaje del precio actual.

- **Ruta:** `/api/admin/editProductPrice`
- **Método:** POST
- **Cuerpo de la solicitud:** Debe incluir los siguientes campos:
  - `startId` (ID de inicio del rango).
  - `endId` (ID de fin del rango).
  - `updateValue` (el nuevo precio o porcentaje de cambio).
  - `isPercentage` (booleano que indica si `updateValue` es un porcentaje).

- **Respuesta exitosa (200 OK):** Devuelve un mensaje indicando que los precios se actualizaron con éxito.

- **Posibles respuestas de error:**
  - 400 Bad Request: Si `startId`, `endId`, o `updateValue` no son números válidos.
  - 404 Not Found: Si no se encuentran productos dentro del rango especificado.

Cuando `isPercentage` es `true`, el nuevo precio se calcula como un porcentaje del precio actual, y cuando es `false`, `updateValue` se establece como el nuevo precio absoluto. Este endpoint es útil para realizar actualizaciones masivas de precios en productos dentro de un rango específico.

### Editar Precios de Productos por Categoría 

- **Descripción:** Este endpoint permite editar los precios de los productos que pertenecen a una categoría específica. Al igual que el método `editProductPrice`, puedes elegir si deseas actualizar el precio de manera absoluta o como un porcentaje del precio actual.

- **Ruta:** `/api/admin/editProductPriceByCategory`
- **Método:** POST
- **Cuerpo de la solicitud:** Debe incluir los siguientes campos:
  - `categoryId` (ID de la categoría a la que pertenecen los productos).
  - `updateValue` (el nuevo precio o porcentaje de cambio).
  - `isPercentage` (booleano que indica si `updateValue` es un porcentaje).

- **Respuesta exitosa (200 OK):** Devuelve un mensaje indicando que los precios se actualizaron con éxito para la categoría especificada.

- **Posibles respuestas de error:**
  - 400 Bad Request: Si `categoryId` o `updateValue` no se proporcionan.
  - 404 Not Found: Si no se encuentran productos en la categoría especificada.

Este endpoint es útil para actualizar los precios de todos los productos dentro de una categoría en particular, ya sea como un valor absoluto o como un porcentaje. Puedes usarlo para realizar ajustes masivos de precios dentro de una categoría específica en tu sistema.

Asegúrate de que los usuarios de tu API comprendan claramente cómo utilizar estos endpoints y las implicaciones de la actualización de precios de productos.


## Controladores

Los siguientes metodos de los controladores manejan las solicitudes a los endpoints de administración:

- `showListUsers`: Obtiene la lista de usuarios.
- `showListProducts`: Obtiene la lista de productos.
- `createProduct`: Crea un nuevo producto.
- `deleteProduct`: Elimina un producto.
- `getEditProduct`: Obtiene detalles de un producto para su edición.
- `saveEditProduct`: Guarda la edición de un producto.
- `editProductPrice`: Edita el precio de varios productos.
- `editProductPriceByCategory`: Edita el precio de productos por categoría.

### Ejemplos de Uso

A continuación, se presentan ejemplos de solicitudes y respuestas para los endpoints de administración:

**Obtener la lista de usuarios (GET /api/admin/users)**

```json
{
  "ok": true,
  "data": [...],  // Lista de usuarios
  "meta": {
    "status": 200,
    "total": 5
  }
}

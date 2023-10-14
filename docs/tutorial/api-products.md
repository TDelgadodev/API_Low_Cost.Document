---
sidebar_position: 3
---

# API Products

Esta API proporciona endpoints para acceder a información detallada sobre productos, buscar productos por diferentes criterios, y obtener detalles sobre marcas y categorías. A continuación se describen los endpoints disponibles:

### Obtener Detalles de un Producto

- **Descripción**: Este endpoint permite obtener información detallada sobre un producto específico a través de su ID.
- **Ruta**: /api/products/:id
- **Método**: GET
- **Respuesta exitos**a (código 200):
    ```json
    {
        "ok": true,
        "data": {
            "id": 1,
            "name": "Ejemplo de Producto",
            "price": 19.99,
            "description": "Este es un producto de ejemplo.",
        "category": {
            "id": 1,
            "name": "Electrónicos"
        },
        "brand": {
            "id": 1,
            "name": "Ejemplo Brand"
            }
        },
        "meta": {
            "status": 200,
            "total": 1
        }   
  }
    ```

### Buscar Productos por Palabra Clave

- **Descripción**: Buscar productos que coincidan con una palabra clave proporcionada en el nombre o la descripción.
- **Ruta**: /api/products/search?keyword={keyword}
- **Método**: GET
- **Respuesta exitos**a (código 200):   
    ```json
        {
            "ok": true,
            "data": [
                {
                  "id": 1,
                  "name": "Ejemplo de Producto 1",
                  "price": 19.99,
                  "description": "Este es un producto de ejemplo 1."
                },
                {
                  "id": 2,
                  "name": "Ejemplo de Producto 2",
                  "price": 29.99,
                  "description": "Este es un producto de ejemplo 2."
                }
            ],
        },
        {
            "meta": {
                "status": 200,
                "total": 2,
                "keyword": "ejemplo"
            }
        }
    ```

- **Código de Estado**: 400 (Bad Request)
- Respuesta JSON con un mensaje de error si la palabra clave no se proporciona.
    ```json
    {
        "ok": false,
        "message": "Por favor, proporcione un keyword válido en la consulta."
    }
    ```

### Buscar Productos por Categoria

- **Descripción**: Buscar productos que pertenecen a una categoría específica.
- **Ruta**: /api/products/category/:id
- **Método**: GET
- **Respuesta exitos**a (código 200):
    ```json
        {
            "ok": true,
            "data": [
            {
                "id": 1,
                "name": "Producto A",
                "price": 29.99,
                "description": "Este es el producto A."
            },
            {
                "id": 2,
                "name": "Producto B",
                "price": 39.99,
                "description": "Este es el producto B."
            }
            ],
            "meta": {
                "status": 200,
                "total": 2
            }
        }
    ```
- **Código de Estado**: 404 (Not Found)
- Respuesta JSON con un mensaje de error si no se encuentran productos en la categoría especificada.
    ```json
        {
            "ok": false,
            "message": "No se encontraron productos en la categoría especificada."
        }
    ```

### Buscar productos por Marca

- **Descripción**: Buscar productos de una marca específica.
- **Ruta**: /api/products/brand/:id
- **Método**: GET
- **Respuesta exitos**a (código 200):
    - Respuesta JSON con la lista de productos de la marca especificada:

    ```json
        {
            "ok": true,
            "data": [
                {
                    "id": 1,
                    "name": "Producto X",
                    "price": 19.99,
                    "description": "Este es el producto X."
                },
                {
                    "id": 2,
                    "name": "Producto Y",
                    "price": 24.99,
                    "description": "Este es el producto Y."
                }
            ],
            "meta": {
                "status": 200,
                "total": 2
            }
        }
    ```
- **Código de Estado**: 404 (Not Found)
    - Respuesta JSON con un mensaje de error si no se encuentran productos de la marca especificada:
         ```json
        {
            "ok": false,
            "message": "No se encontraron productos de la marca especificada."
        }
        ```


### Obtener Productos en Oferta

- **Descripción**: Obtener una lista de productos que están en oferta.
- **Ruta**: /api/products/offer
- **Método**: GET
- **Respuesta exitos**a (código 200):
    - Respuesta JSON con la lista de productos en oferta:
        ```json
            {
                "ok": true,
                "data": [
                    {
                        "id": 1,
                        "name": "Producto Oferta 1",
                        "price": 9.99,
                        "description": "Este es un producto en oferta 1."
                    },
                    {
                        "id": 2,
                        "name": "Producto Oferta 2",
                        "price": 14.99,
                        "description": "Este es un producto en oferta 2."
                    }
                ],
                "meta": {
                    "status": 200,
                    "total": 2
                }
            }
        ```

- **Código de Estado**: 404 (Not Found)
- Respuesta JSON con un mensaje de error si no se encuentran productos en oferta:
    ```json
        {
            "ok": false,
            "message": "No se encontraron productos en oferta."
        }

    ```


### Obtener Todas las Marcas

- **Descripción**: Obtener una lista de todas las marcas de productos disponibles.
- **Ruta**: /api/products/brands
- **Método**: GET
- **Código de Estado**: 200 (OK)
    Respuesta JSON con la lista de marcas:
    ```json
        {
            "ok": true,
            "data": [
                {
                    "id": 1,
                    "name": "Marca A"
                },
                {
                    "id": 2,
                    "name": "Marca B"
                }
            ],
            "meta": {
                "status": 200,
                "total": 2
            }
        }
    ```

- **Código de Estado**: 404 (Not Found)
    - Respuesta JSON con un mensaje de error si no se encuentran marcas:
        ```json
            {
                "ok": false,
                "message": "No se encontraron marcas."
            }

        ```

### Obtener Todas las Categorías

- **Descripción**: Obtener una lista de todas las categorías de productos disponibles.
- **Ruta**: /api/products/categories
- **Método**: GET
- **Código de Estado**: 200 (OK)
    - Respuesta JSON con la lista de categorías.
    ```json
    {
        "ok": true,
        "data": [
            {
            "id": 1,
            "name": "Categoría A"
            },
            {
            "id": 2,
            "name": "Categoría B"
            }
        ],
        "meta": {
            "status": 200,
            "total": 2
        }
    }
    ```

- **Código de Estado**: 404 (Not Found)
    - Respuesta JSON con un mensaje de error si no se encuentran categorías.
    ```json
        {
            "ok": false,
            "message": "No se encontraron categorías."
        }
    ```

### Obtener el Último Producto

- **Descripción****: Obtener información sobre el último producto agregado a la base de datos.
- **Ruta****: /api/products/getLastProduct
- **Método****: GET
- **Código de Estado****: 200 (OK)
    - Respuesta JSON con los detalles del último producto:
        ```json
        {
        "ok": true,
        "data": {
        "id": 1,
        "name": "Último Producto",
        "price": 49.99,
        "description": "Este es el producto más reciente."
        },
        "meta": {
            "status": 200
        }
        }
        ```
- **Código de Estado**: 404 (Not Found)
- Respuesta JSON con un mensaje de error si no se encuentra ningún producto en la base de datos:    
    ```json
            {
                "ok": false,
                "message": "No se encontró ningún producto en la base de datos."
                }
    ```
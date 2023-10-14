---
sidebar_position: 2
---

# API User

Esta API facilita la interacción con los datos de los usuarios, permitiéndoles registrarse, acceder, actualizar su perfil, verificar sus correos electrónicos, restablecer contraseñas y finalizar compras.

A continuación, encontrarás detalles sobre los distintos endpoints y operaciones disponibles para los usuarios.

## Usuarios (/api/users)

### Registro de Usuario
- Descripción: Registra un nuevo usuario en la plataforma.
- Ruta: /register
- Método HTTP: POST
- Parámetros de solicitud:
    - name (cadena): Nombre del usuario.    
    - surname (cadena): Apellido del usuario.
    - email (cadena): Correo electrónico del usuario.
    - password (cadena): Contraseña del usuario.
    - phone (cadena): Número de teléfono del usuario.

- Respuesta exitosa (código 200):
```json
{
    "ok": true,
    "message": "Usuario registrado con exito!",
    "data": {
        "newUser": {
            "checked": false,
            "shopping": 0,
            "id": 5,
            "name": "Thiago",
            "surname": "Delgado",
            "email": "thiago@gmail.com",
            "phone": "123456",
            "password": "$2a$10$21VEi/Uu.TflT1a865Cws.WNwi8CusRL/4VlBdVK236boNsaU9ooq",
            "rolId": 2,
            "addressId": 5,
            "updatedAt": "2023-10-13T13:52:41.800Z",
            "createdAt": "2023-10-13T13:52:41.794Z",
            "token": "7nl8qfqjevg1hckkv3q8"
        }
    }
}
```

### Inicio de sesión de Usuario

- Descripción: Actualiza la información del usuario, incluyendo nombre, apellido, teléfono, DNI y dirección.
- Ruta: /login
- Método HTTP: POST
- Parámetros de solicitud:
    - email (cadena): Correo electrónico del usuario.
    - password (cadena): Contraseña del usuario.
    - Respuesta exitosa (código 200):
    ```json
    {
    "ok": true,
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyIjp7ImlkIjo1LCJuYW1lIjoiVGhpYWdvIiwiZW1haWwiOiJ0aGlhZ29AZ21haWwuY29tIiwicm9sSWQiOjJ9LCJpYXQiOjE2OTcyMDU0MDUsImV4cCI6MTY5NzIwNTY0NX0.XW6L_ATO2Tw5AGgaTE-_Hlk2DrPLCsNUj-7I9wtS1l8"
    }
    ```  

### Actualización de Datos de Usuario

- Descripción: Permite a un usuario actualizar su información de perfil.
- Ruta: /:id (donde :id es el ID del usuario)
- Método HTTP: PUT
- Parámetros de solicitud:
    - id: El ID del usuario.
    - name: Nombre del usuario.
    - surname: Apellido del usuario.
    - phone: Número de teléfono del usuario.
    - dni: Número de documento de identidad del usuario.
    - address: Objeto que contiene información de dirección del usuario.
        - street: Calle de la dirección.
        - numberAddress: Número de dirección.
        - postCode: Código postal de la dirección.

- Respuestas: 
    - Éxito (200 OK): Se ha actualizado la información del usuario correctamente:
        ```json
        {
            "ok": true,
            "message": "Usuario modificado con éxito",
            "user": "Datos actualizados del usuario, incluyendo ID, nombre, apellido, DNI, teléfono y dirección."
            "meta": {
                "status": 200
                "total": 1
                "url": "URL para acceder al perfil del usuario actualizado."
            }
        }
        ```  
    - Error de Cliente (400 Bad Request): El ID del usuario es inválido o faltan datos obligatorios:
        ```json
              {
                "ok": false
                "error": {
                    "status": 400
                    "message": "Mensaje de error específico."
                }
              }
        ```

    - Error de Servidor (500 Internal Server Error): Se produjo un error interno durante la actualización.
        ```json
              {
                "ok": false
                "error": "Error interno del servidor"
              }
        ```

### Verificación de Usuario por Correo Electrónico

- Verificación de Usuario por Correo Electrónico
- Ruta: /verify
- Método HTTP: GET
- Parámetros de solicitud:
    - email (cadena): Correo electrónico del usuario a verificar.
- Respuesta exitosa (código 200):
    ```json
  {
      "ok": true,
      "data": {
          "userExist": true
       }
  }
    ```
Si el usuario con el correo electrónico proporcionado no se encuentra en la base de datos, se recibirá una respuesta con un código de estado `404` (Not Found) indicando que el recurso solicitado (el usuario) no existe. A continuación, se proporciona una descripción del caso malo:
- Código de Estado: 404
- Respuesta:
  ```json
  {
    "ok": false,
    "error": {
      "status": 404,
      "message": "El usuario con el correo electrónico [correo] no fue encontrado."
    }
  }
 
### Perfil de Usuario

- Descripción: Obtiene información detallada del perfil de un usuario.
- Ruta: /profile/:id (donde :id es el ID del usuario)
- Método HTTP: GET
- Respuesta exitosa (código 200):
```json
{
    "ok": true,
    "user": {
        "id": 1,
        "name": "nombre de ejemplo",
        "surname": "apellido de ejemplo",
        "password": "$2a$10$.pNleskb/seADaNIsHgfTO0BmgEQ35gp7eubz6D4qkBnCXUQLUgJO",
        "token": "token de ejemplo",
        "checked": null,
        "phone": 1139034290,
        "dni": null,
        "email": "email@test.com",
        "resetCode": null,
        "rolId": 1,
        "addressId": 1,
        "shopping": null,
        "createdAt": "2023-09-29T13:00:47.000Z",
        "updatedAt": "2023-09-29T13:00:47.000Z",
        "address": {
            "id": 1,
            "street": "Calle Falsa",
            "numberAddress": 1234,
            "postCode": 1234,
            "createdAt": "2023-09-29T13:00:47.000Z",
            "updatedAt": "2023-09-29T13:00:47.000Z"
        }
    }
}
```

### Solicitud de Código para Restablecer Contraseña

- Descripción: Permite a un usuario solicitar un código via email para restablecer su contraseña.
- Ruta: /auth/reset-password/:email (donde :email es la dirección de correo electrónico)
- Método HTTP: POST
- Respuesta exitosa (código 200):
    - ejemplo: 
        ```json
        {
          "ok": true,
          "message": "Mensaje enviado"
        }
        ```     

### Finalizar la compra

- Descripción: Permite a un usuario finalizar una compra y envía notificaciones por correo electrónico.
- Ruta: /finish-purchase
- Método HTTP: POST
- Parámetros de solicitud:
    - values (objeto): Detalles del comprador (nombre, apellido, correo electrónico, etc.).
    - cartItems (arreglo de objetos): Detalles de los elementos del carrito de compra.

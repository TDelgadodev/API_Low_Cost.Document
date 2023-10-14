---
sidebar_position: 2
---

# Integración de Mercado Pago

El sistema incluye una integración con Mercado Pago para procesar pagos de productos. A continuación, se describen las API y sus respectivas operaciones relacionadas con Mercado Pago.

## API de Mercado Pago

### Crear Preferencia de Pago

- **Descripción:** Esta API permite crear una preferencia de pago en Mercado Pago. Se pueden especificar los detalles del producto, como su descripción, precio y cantidad.

- **Ruta:** `/mp/create_preference`
- **Método:** POST
- **Cuerpo de la solicitud:** Debe contener los detalles del producto, como la descripción, precio y cantidad.
- **Respuesta exitosa (200 OK):** Devuelve una preferencia de pago generada por Mercado Pago.

### Información del Comprador

- **Descripción:** Esta API permite enviar la información del comprador al servidor, que se utilizará posteriormente para completar la compra en Mercado Pago.

- **Ruta:** `/mp/buyer_info`
- **Método:** POST
- **Cuerpo de la solicitud:** Debe contener la información del comprador.
- **Respuesta exitosa (200 OK):** Almacena la información del comprador para su posterior uso.

### Compra Exitosa

- **Descripción:** Esta API procesa la respuesta de Mercado Pago después de que un comprador ha realizado una compra con éxito.

- **Ruta:** `/mp/success`
- **Método:** GET
- **Respuesta exitosa (200 OK):** Actualiza la información del usuario y envía correos electrónicos de confirmación de compra al comprador y al vendedor.

## Consideraciones Importantes

- Se utiliza una configuración de acceso a Mercado Pago de prueba (`access_token: "TEST-2938245235269496-091414-6edd5c1f1294b94467a89c6b720d2d7f-1479550679"`) en el código de ejemplo. Debes configurar las credenciales reales de Mercado Pago para entorno de producción en su lugar.

- La integración de Mercado Pago permite a los usuarios realizar compras en tu aplicación y recibir notificaciones de compra exitosa o denegada.

- La información del comprador se almacena temporalmente en el servidor y se utiliza para actualizar el historial de compras del usuario y enviar correos electrónicos de confirmación.

- La respuesta de compra exitosa de Mercado Pago se procesa para actualizar el historial de compras del usuario y notificar al vendedor y al comprador sobre la compra.

Asegúrate de seguir las mejores prácticas de seguridad y configurar adecuadamente las credenciales de Mercado Pago para garantizar un procesamiento de pagos seguro en tu aplicación.


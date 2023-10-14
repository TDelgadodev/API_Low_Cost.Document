---
sidebar_position: 1
---

# Instalación de la API Low Cost

La API Low Cost está diseñada para ser fácil de instalar y usar. A continuación, te guiamos a través del proceso de instalación.

:::info Importante
Recomendamos encarecidamente utilizar la API Low Cost v2 para aprovechar las últimas características y mejoras.
:::

### Requisitos Previos

Asegúrate de tener instalada la última versión de Node.js. También recomendamos la instalación de Yarn.

- [Node.js](https://nodejs.org/en/download/): Versión 16.14 o superior.
  - Al instalar Node.js, te recomendamos marcar todas las casillas relacionadas con las dependencias.

Asegúrate de tener Node >= 10.9.0 y Yarn >= 1.5.

### Estructura de Directorios

Antes de instalar la API Low Cost, es importante comprender la estructura de directorios de tu proyecto. A continuación, se muestra una vista general de las carpetas y archivos clave en tu proyecto:
```
weblowcost
├── .env.example
├── .gitignore
├── .sequelizerc
├── package.json
├── public
│ └── ... (recursos públicos)
├── src
│ ├── bin
│ ├── controllers
│ ├── database
│ ├── helpers
│ ├── middlewares
│ ├── routes
│ ├── services
│ ├── app.js
│ └── ...
```

## Instalación de la API Low Cost

Para ejecutar la API Low Cost en tu entorno de desarrollo, sigue estos pasos básicos:

### 1. Clonar el Repositorio

Clona el proyecto desde el repositorio en GitHub:

```bash
git clone https://github.com/gnicolaslan/webLowCost
```
### 2. Instalacion de dependencias
Instala las dependencias del proyecto utilizando npm o yarn:
```bash
npm install
# O
yarn install
```

### 3. Configurar las Variables de Entorno
Copia el archivo .env.example como .env y completa las variables de entorno con tu información

### 4. Inicie el servidor
Inicia el servidor con el siguiente comando:
```bash
npm run start
# O
yarn run start
```
¡Con estos pasos, tendrás el servidor de la API Low Cost en funcionamiento en tu entorno de desarrollo! Si tienes alguna pregunta, consulta el archivo README en el repositorio para obtener más detalles.

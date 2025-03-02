# 📌 Reto Técnico - Vue.js 3

## 📖 Índice
* [1. Acerca del proyecto](#1-acerca-del-proyecto)
* [2. Características](#2-características)
* [3. Instalación y configuración](#3-instalación-y-configuración)
* [4. Prototipos en Figma](#4-prototipos-en-figma)
* [5. Uso del Proyecto](#4-uso-del-proyecto)
    * [Pantalla de Listado](#5-pantalla-de-listado)
    * [Pantalla de Detalle del Post](#6-pantalla-de-listado)
* [6. Despliegue en Amazon Web Services](#5-despliegue-en-amazon-web-services)
* [7. Tecnologías Utilizadas](#7-tecnologías-utilizadas)

## 1. Acerca del Proyecto

Este proyecto es una aplicación web desarrollada con Vue.js 3 que permite visualizar un listado de publicaciones (posts) obtenidas desde la API de JSONPlaceholder. Cada publicación cuenta con atributos como título, contenido y número de visitas.

Además, al hacer clic en un post, se abre un modal (pop-up) que muestra los detalles de la publicación junto con sus comentarios.

Objetivo: Implementar una interfaz dinámica, rápida y eficiente para visualizar y gestionar publicaciones con un contador de visitas.

## 2. Características

* Listado de posts con título y contenido.
* Contador de visitas almacenado en localStorage.
* Modal con detalles del post y comentarios.
* Diseño responsivo y estilizado con CSS y Figma.
* Manejo de estados con Vue.js y props.
* Uso de fetch para consumir API externa.

## 3. Instalación y Configuración

1️⃣ Clonar el repositorio

```sh
 git clone https://github.com/YahairaPerez1994/RetoTecnico-VueJS.git
```

2️⃣ Ingresar al directorio del proyecto

```sh
cd yahaira/vue-posts-app
```

3️⃣ Instalar dependencias

```sh
npm install
```

4️⃣ Ejecutar el servidor de desarrollo

```sh
npm run dev
```

5️⃣ Abrir en el navegador

El proyecto estará disponible en: `http://localhost:5173/` 

## 4. Prototipos en Figma

El diseño de la interfaz se realizó en `Figma`, asegurando una experiencia de usuario intuitiva y un diseño responsivo.

## 5. Uso del Proyecto

## 📌 Pantalla de Listado
Muestra una lista de publicaciones con título y contenido.
Al hacer clic en un post, se abre un modal con la información detallada.
Se obtiene la data desde la API de JSONPlaceholder.

![image](https://github.com/user-attachments/assets/16a87a8c-7569-40a2-9176-45ef8db923b7)



## 📌 Pantalla de Detalle del Post
Se abre en un modal.
Muestra título, contenido y número de visitas.
También carga los comentarios del post desde la API.
Se almacena y actualiza el contador de visitas en localStorage.

![image](https://github.com/user-attachments/assets/b3237949-7337-4e58-b565-f8cac9f8a1ca)


## 6. Despliegue en Amazon Web Services

El proyecto está implementado en `AWS Amplify` , que está directamente conectado al repositorio en `GitHub` a través de la rama main. Se ha configurado un despliegue continuo `(CI/CD)` , lo que significa que cualquier actualización en la rama main se detecta automáticamente y se implementa en el entorno de producción sin intervención manual.

Además, `AWS Amplify` gestiona el hosting de la aplicación con una infraestructura escalable y segura, optimizando el rendimiento de la interfaz en la web.

🔗 URL del despliegue: https://main.d3ka7tkxhkn5lm.amplifyapp.com/


## 7. Tecnologías Utilizadas

* Vue.js 3 - Framework de JavaScript.
* CSS / Tailwind CSS - Estilos y diseño responsivo.
* Fetch API - Para consumir la API de posts y comentarios.
* Figma - Diseño de la interfaz de usuario.
* localStorage - Para almacenar el número de visitas.
* Git & GitHub - Control de versiones y colaboración.

📌 ¡Gracias por visitar este proyecto! 🎉 Si tienes alguna duda o sugerencia, siéntete libre de abrir un issue en GitHub o contactarme. 🚀

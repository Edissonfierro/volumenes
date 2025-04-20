
# Práctica Volúmenes

Persistencia de Datos en Contenedores PostgreSQL con y sin Volúmenes en Docker

## 2. Tiempo de duración  
**Tiempo estimado:** 30 minutos
## 3. Fundamentos  
**¿Qué es un volumen en Docker?**

Según Marcia ramos en el repositorio de kinsta, los volúmenes en Docker son esenciales para almacenar datos persistentes generados por contenedores efímeros, asegurando que los datos no se pierdan al eliminar o actualizar un contenedor. A diferencia de los montajes vinculados, los volúmenes están desacoplados del sistema de archivos del contenedor, lo que facilita su portabilidad, gestión y migración entre diferentes hosts y contenedores. Además, permiten realizar copias de seguridad y compartir datos entre contenedores, siendo compatibles con diversos controladores de almacenamiento para adaptarse a diferentes necesidades.

**¿Cuál es la diferencia entre un gestor de base de datos y un motor de base de datos?**
**Tiempo estimado:**

Según el artículo de MOTORBA, la diferencia entre un motor y un gestor de base de datos radica en sus roles dentro del sistema:

Gestor de Base de Datos (DBMS): Es el software que facilita la creación, administración y acceso a las bases de datos. Ofrece una interfaz que permite gestionar los datos de manera sencilla, incluyendo tareas como definir la estructura de la base de datos, manipular los datos y controlar el acceso y la seguridad.

Motor de Base de Datos: Este componente es el encargado de las operaciones fundamentales como el almacenamiento, la recuperación y la gestión de los datos. Se considera el "corazón" del DBMS, pues realiza las tareas técnicas que permiten que la base de datos funcione correctamente, como almacenar y recuperar información de manera eficiente.

**¿Cuál es el ciclo de vida de un contenedor Docker?**

El ciclo de vida de una aplicación en Docker consta de seis pasos clave:

Desarrollo de la aplicación: Se crea el código fuente de la aplicación, como una página web estática, que será el núcleo de la aplicación que se ejecutará en el contenedor.

Creación de la imagen Docker: Usando un archivo Dockerfile, se define la imagen base, se instalan los paquetes necesarios y se copia el código fuente al contenedor para que esté listo para ejecutarse.

Pruebas en el entorno de desarrollo: Se construye la imagen y se ejecuta un contenedor para asegurarse de que la aplicación funcione correctamente antes de pasar a producción.

Distribución de la imagen: Una vez que la imagen está lista, se sube a un registro como Docker Hub, lo que facilita su acceso y despliegue en otros entornos.

Implantación en producción: La imagen se descarga del registro y se ejecuta en el entorno de producción, asegurando que la aplicación esté disponible para los usuarios finales.

Modificación y actualización: Si es necesario realizar cambios o mejoras en la aplicación, se actualiza el código fuente y el Dockerfile, se reconstruye la imagen y se repiten los pasos para desplegar la nueva versión.



## 4. Conocimientos previos

Para realizar esta práctica, el estudiante necesita tener claro los siguientes temas:

- Comandos Linux básicos (navegación, creación de archivos, permisos).
- Manejo de navegador web.
- Edición de archivos con editores simples (Nano, VS Code).
- Conceptos básicos de redes y puertos.

## 5. Objetivos a alcanzar

Implementar un contenedor de base de datos PostgreSQL utilizando Docker.

Comprender el comportamiento de los datos al eliminar un contenedor sin volumen.

Crear y administrar volúmenes en Docker para lograr la persistencia de datos.

Verificar la persistencia de datos en un contenedor PostgreSQL al utilizar volúmenes.


## 6. Equipo necesario

- Computador con sistema operativo **Windows/Linux/Mac**.
- Conexión a Internet.
- Docker instalado 
- Cuenta en [Docker Play](https://labs.play-with-docker.com) (opcional).
- Navegador web actualizado.
- Editor de texto (VS Code, Sublime Text, etc.).

## 7. Material de apoyo

- Documentación oficial de Docker: https://docs.docker.com  
- Guía de la asignatura.  
- Linux Cheat Sheet: https://github.com/LeCoupa/awesome-cheatsheets  
- Documentación oficial de Nginx: https://nginx.org/en/docs  

## 8. Procedimiento

🔸 Parte 1: Base de datos sin volumen

1. Crear un contenedor PostgreSQL con el nombre `server_db1`.
(https://github.com/Edissonfierro/volumenes/blob/main/1.jpg)


2. Conectar un administrador de base de datos (como DataGrip o TablePlus) al contenedor `server_db1`.
3. Crear una base de datos llamada `test`.
4. En la base de datos `test`, crear una tabla llamada `customer` con los campos: `id`, `fullname` y `status`.
5. Insertar al menos un registro en la tabla `customer`.
6. Detener y eliminar el contenedor `server_db1`.
7. Volver a crear el contenedor PostgreSQL con el mismo nombre `server_db1`.
8. Conectarse nuevamente desde el administrador de base de datos.
9. Verificar que la base de datos `test` ya no existe, demostrando que los datos no se han conservado.



🔸 Parte 2: Base de datos con volumen

1. Crear un volumen en Docker con el comando:
2. Crear un contenedor PostgreSQL con el nombre `server_db2`, asociando el volumen creado.
3. Conectarse al contenedor con DataGrip o TablePlus.
4. Crear la base de datos `test`.
5. Crear la tabla `customer` con los campos: `id`, `fullname` y `status`.
6. Insertar al menos un registro en la tabla.
7. Detener y eliminar el contenedor `server_db2`.
8. Volver a crear el contenedor `server_db2` usando el volumen `pgdata` nuevamente.
9. Conectarse desde el administrador de base de datos y verificar que la base de datos `test` y los registros han persistido.




## 9. Resultados esperados:

El resultado esperado es ver que, sin volúmenes, los datos en PostgreSQL se pierden cuando se elimina el contenedor, pero al usar volúmenes, los datos permanecen intactos incluso después de eliminar y recrear el contenedor.

## 10. Bibliografía

Ramos, M. (2023, 11 de septiembre). Uso de volúmenes para gestionar datos persistentes con Docker Compose. Kinsta. https://kinsta.com/es/blog/volumenes-docker-compose/

MOTORBA. (n.d.). Diferencia entre motor y gestor de base de datos. MOTORBA. Recuperado el 20 de abril de 2025, de https://motorba.com.ar/diferencia-entre-motor-y-gestor-de-base-de-datos/

IESGN. (2021). Ciclo de vida de un contenedor Docker. IESGN. Recuperado el 20 de abril de 2025, de https://iesgn.github.io/curso_docker_2021/sesion6/ciclo_vida.html

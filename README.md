# Ecommerce Frutos de la Tierra

Este proyecto es una aplicación web que simula una tienda en línea (E-commerce). Cuenta con un catálogo interactivo de productos ordenados por categorías, un carrito de compras funcional y un sistema dinámico de gestión (ABM) tanto para productos como para categorías enlazado a una base de datos relacional.

## Tecnologías Utilizadas

### Para el Backend
* **Java 17** con **Spring Boot**
* **Spring Data JPA** (Persistencia y consultas parametrizadas seguras)
* **MySQL** (Motor de base de datos)

### Para el Frontend
* **HTML5** y **CSS3** (Diseño moderno responsive por grillas y pestañas)
* **JavaScript Moderno (ES6+)** (Consumo asíncrono de APIs mediante `fetch`)

---

## Características Principales

* **Listado por Categorías:** Los productos se agrupan automáticamente bajo su respectiva categoría.
* **Buscadores Integrados:** 
  * Búsqueda nativa de productos por nombre conectada al Backend (`/productos/nombre/{nombre}`).
  * Filtrado de categorías en tiempo real en el Frontend.
* **Control de Stock Dinámico:** Si un producto tiene `stock: 0`, el botón de compra se deshabilita automáticamente mostrando el cartel "Sin Stock".
* **Seguridad (Antinyección SQL):** Implementación de consultas parametrizadas nativas mediante los repositorios de Spring para bloquear inyecciones de código malicioso.
* **Gestión Segura (ABM):** Formularios limpios post-acción, previsualización de imágenes en bajas y validación de integridad referencial (no se permite borrar categorías con productos asociados).

---

## Endpoints Disponibles (API REST)

| Método | Endpoint | Descripción |
|--------|----------|-------------|
| **GET** | `/productos` | Lista todos los productos |
| **GET** | `/productos/{id}` | Obtiene un producto específico |
| **POST** | `/productos` | Crea un nuevo producto |
| **PUT** | `/productos/{id}` | Actualiza un producto existente |
| **DELETE** | `/productos/{id}` | Elimina un producto por ID |
| **GET** | `/productos/nombre/{nombre}` | Busca productos por coincidencia de nombre |
| **GET** | `/categorias` | Lista todas las categorías |
| **POST** | `/categorias` | Crea una nueva categoría |
| **PUT** | `/categorias/{id}` | Actualiza una categoría |
| **DELETE** | `/categorias/{id}` | Elimina una categoría (Valida relación) |
| **POST** | `/carritos` | Crea un carrito vacío |
| **GET** | `/carritos/{id}` | Obtiene un carrito con sus productos |
| **POST** | `/carritos/{cId}/productos/{pId}` | Agrega un producto al carrito |
| **DELETE** | `/carritos/{id}/vaciar` | Vacía todos los ítems del carrito |
| **DELETE** | `/carritos/{id}` | Elimina el carrito por completo |

---

## Inicialización de Datos 

El sistema cuenta con una precarga automática en el Backend para llenar la base de datos con un catálogo inicial de frutos secos organizado de la siguiente manera:
* **Fruta Seca:** Nueces, Almendras, Pasas rubias/negras, Ciruelas, etc.
* **Varios:** Granola Premium, Aceite de Coco, Crema de Maní, etc.

---

## Cómo Ejecutar el Proyecto


1. Clonar el repositorio
git clone [https://github.com/Adrilu-web/ecommerce-FrontEnd.git](https://github.com/Adrilu-web/ecommerce-FrontEnd.git)
cd ecommerce-FrontEnd

2. Configurar y Levantar el Backend (Spring Boot)
- Requisito previo: tener instalado Java 17 (o superior) y MySQL Server corriendo en tu máquina.
- Base de Datos: Abrír la terminal de MySQL o una herramienta como Workbench y crear la base de datos para el proyecto:

  ```
  CREATE DATABASE ecommerce_db;
  ```

- Configuración: Revisar el archivo src/main/resources/application.properties en el proyecto de Spring Boot y configurar usuario y contraseña de MySQL:

    ```
    spring.datasource.url=jdbc:mysql://localhost:3360/ecommerce_db
    spring.datasource.username=TU_USUARIO_MYSQL
    spring.datasource.password=TU_CONTRASEÑA_MYSQL
    spring.jpa.hibernate.ddl-auto=update
    ```

- Ejecución: Abrir el proyecto de Backend en tu IDE favorito (IntelliJ IDEA, Eclipse o VS Code) y ejecutar la clase principal (la que tiene la anotación @SpringBootApplication). Al levantar, se crearán las tablas y se cargarán automáticamente los productos de frutos secos en la base de datos.

  - El backend quedará escuchando en: http://localhost:8080

3. Ejecutar el Frontend (Interfaz Web)
Como el Frontend está desarrollado con tecnologías nativas del navegador (HTML, CSS y JavaScript), no requiere de consolas ni de instalaciones complejas de Node.js.
Hay dos opciones para ejecutarlo:

- Opción A: Abrir directamente (Local)
Buscar en el explorador de archivos y hacer doble clic sobre el archivo index.html para abrirlo en el navegador web predeterminado (Chrome, Edge, Firefox, etc.).

- Opción B: Usar Live Server (Recomendado para Desarrollo)
Si usás Visual Studio Code, podés instalar la extensión Live Server:

  - Abrir la carpeta del proyecto en VS Code.
  - Haz clic derecho sobre index.html.
  - Seleccionar "Open with Live Server".
  - Esto levantará un servidor local rápido (normalmente en http://127.0.0.1:5500) que recargará la página automáticamente cada vez que se haga un cambio en el código.
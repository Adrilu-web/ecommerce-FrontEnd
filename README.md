# 🛒 Ecommerce Frutos de la Tierra

Este proyecto es una aplicación web que simula una tienda en línea (E-commerce). Cuenta con un catálogo interactivo de productos ordenados por categorías, un carrito de compras funcional y un sistema dinámico de gestión (ABM) tanto para productos como para categorías enlazado a una base de datos relacional.

## Tecnologías Utilizadas

### Backend
* **Java 17** con **Spring Boot**
* **Spring Data JPA** (Persistencia y consultas parametrizadas seguras)
* **MySQL** (Motor de base de datos)

### Frontend
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
* **Fruta Seca:** Nueces, Almendras, Pasas rubias/negras, Ciruelas, Castañas, Dátiles y Pistachos.
* **Varios:** Granola Premium, Aceite de Coco (Neutro/Virgen), Miel Orgánica, Crema de Maní y Hummus.

---

## 💻 Cómo Ejecutar el Proyecto

### 1. Clonar el repositorio
```bash
git clone [https://github.com/TU_USUARIO/TU_REPOSITORIO.git](https://github.com/TU_USUARIO/TU_REPOSITORIO.git)
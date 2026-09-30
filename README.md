# Ejercicio — Base de Datos de Gestión de Biblioteca

Proyecto enfocado en la modelación Entidad-Relación (DER / MER) e implementación de base de datos relacional para un sistema de gestión bibliotecaria, administrando el catálogo de libros, autores, ejemplares físicos, usuarios y préstamos.

---

## Descripción

El sistema modela una estructura de datos relacional para la gestión integral de una biblioteca. Permite vincular obras literarias con sus respectivos autores (soportando relaciones de muchos a muchos a través de una tabla intermedia), gestionar el inventario de ejemplares físicos disponibles, administrar los datos de contacto de los usuarios asociados y llevar el registro histórico y activo de préstamos realizados.

---

## Funcionalidades e Implementación

### Entidades y Atributos

* **Autor:**
* **id_Autor**: Identificador único del autor.
* **Nombre**: Nombre completo del autor.
* **Nacionalidad**: País de origen del autor.
* **Idioma**: Idioma principal de sus obras.
* **Género**: Género literario en el que se destaca.


* **Libro:**
* **id_Libro**: Identificador único del libro.
* **Titulo**: Nombre o título de la obra.
* **Autor**: Nombre de referencia del autor principal.
* **Año de edición**: Año de publicación de la edición.
* **ISBN**: Código identificador estandarizado internacional del libro.


* **Autor - Libro (Tabla Intermedia / Entidad de Relación):**
* **id_Autor - Libro**: Identificador único de la relación.
* **id_Autor**: Clave foránea que referencia al autor.
* **id_Libro**: Clave foránea que referencia al libro.


* **Ejemplar:**
* **id_Ejemplar**: Identificador único de la copia física.
* **Código inventario único**: Código identificador de inventario asignado al ejemplar.
* **Estado**: Condición física o disponibilidad del ejemplar (ej. disponible, prestado, en reparación).


* **Usuario:**
* **id_Usuario**: Identificador único del usuario o socio.
* **Nombre**: Nombre completo del usuario.
* **Teléfono**: Número telefónico de contacto.
* **mail**: Correo electrónico de contacto.
* **N°Legajo**: Número de legajo o carnet institucional.


* **Préstamo:**
* **id_prestamo**: Identificador único de la transacción de préstamo.
* **Fecha de préstamo**: Fecha en la que se retira el ejemplar.
* **Fecha prevista de devolución**: Fecha límite comprometida para la entrega.
* **fecha real de devolución**: Fecha en la que el usuario efectúa la devolución efectiva.
* **Costo**: Importe o canon asociado al préstamo.



---

## Relaciones del Modelo

1. **Autor ↔ Libro (Relación N:M):**
* Un autor puede escribir múltiples libros y un libro puede tener múltiples autores. Se resuelve mediante la entidad intermedia `Autor - Libro` relacionada en esquema `1:N` y `N:1`.


2. **Libro ↔ Ejemplar (Relación 1:N):**
* Un libro registrado en el catálogo puede contar con varios ejemplares físicos asociados en inventario.


3. **Ejemplar ↔ Préstamo (Relación 1:1):**
* Un ejemplar físico específico se asigna individualmente a una transacción de préstamo activa.


4. **Usuario ↔ Préstamo (Relación 1:N):**
* Un usuario registrado puede solicitar e inscribir múltiples préstamos a lo largo del tiempo.

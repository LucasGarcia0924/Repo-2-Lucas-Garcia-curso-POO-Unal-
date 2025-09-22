# Reto 2 POO
Para el segundo reto de la asignatura se pedía un diagrama UML de una situación real, representandolo en clases con sus propios atributos y métodos.

En mi caso escogí el sistema de gestión de una biblioteca, el cuál es el software utilizado tanto por administradores, como personas naturales para interactuar de una u otra forma con los objetos y espacios de la biblioteca.
***

## De manera general

```mermaid
classDiagram
    Usuarios --*  Sistema_de_Gestión_de_una_biblioteca
    Catálogo --*  Sistema_de_Gestión_de_una_biblioteca
    Sistema_de_Prestamos --*  Sistema_de_Gestión_de_una_biblioteca
    Sistema_de_Reservas --*  Sistema_de_Gestión_de_una_biblioteca
 class Sistema_de_Gestión_de_una_biblioteca{
      +lista usuarios
      +Catálogo catálogo
    }
```

## Usuarios
```mermaid
classDiagram
Usuarios <|-- Administradores
class Usuarios{
      +string id
      +string contraseña
      +lista notificaciones por sanciones
      +historial historial individual de préstamos
      +ver catálogo(catálogo)
      +acceder recurso online(catálogo)
      +prestar un libro(catálogo)
      +acceder al sistema de reservas()
    }
    class Administradores{
      +agregar un libro(catálogo)
      +remover un libro(catálogo)
      +procesar devolución(catálogo)
    }
```

## Catálogo
```mermaid
classDiagram
    Libro --*  Catálogo
    Recurso_Online --*  Catálogo
    class Catálogo{
      +lista Libros
      +lista Recursos Online
    }
    class Libro{
      +string Título
      +string Autor
      +string Editorial
      +int edición
      +bool Disponibilidad
      +prestar a(usuarios)
    }
    class Recurso_Online{
      +string Tipo
      +string Título
      +string Autor
      +descargar(usuarios)
    }
```

## Préstamos
```mermaid
classDiagram
Prestamo --*  Historial
Historial --*  Sistema_de_Prestamos: ver historial()
    class Sistema_de_Prestamos{
      +historial historial general de préstamos
      +prohibir prestamos(usuarios)
    }
    class Historial{
    +lista prestamos
    }
    class Prestamo{
      +Libro libros
      +string fecha de préstamos
      +string fecha de vencimiento
      +bool devuelto
      +lista sanciones
    }
```

## Reserva de salas
```mermaid
classDiagram
Sala --*  Sistema_de_Reservas
    Sala <|-- Sala_de_estudio
    Sala <|-- Sala_de_computadores
class Sistema_de_Reservas{
      +ver salas()
    }
    class Sala{
      +bool disponibilidad
      +silla sillas
      +reservar sala()
    }
    class Sala_de_estudio{
      +mesa mesas de trabajo
    }
    class Sala_de_computadores{
      +computador computadores
    }
```
## En conjunto
Finalmente, al unir todas las clases se obtiene la solución general:
```mermaid
classDiagram
    Historial --*  Usuarios: ver historial()
    Historial --*  Sistema_de_Prestamos: ver historial()
    Prestamo --*  Historial
    Sistema_de_Prestamos --> Usuarios : generar sancion()
    Sistema_de_Prestamos --> Libro : actualizar disponibilidad()
    Usuarios <|-- Administradores
    Usuarios --> Catálogo
    Libro --*  Catálogo
    Recurso_Online --*  Catálogo
    Sala --*  Sistema_de_Reservas
    Sala <|-- Sala_de_estudio
    Sala <|-- Sala_de_computadores
    Usuarios --> Sistema_de_Reservas
    Usuarios --*  Sistema_de_Gestión_de_una_biblioteca
    Catálogo --*  Sistema_de_Gestión_de_una_biblioteca
    Sistema_de_Prestamos --*  Sistema_de_Gestión_de_una_biblioteca
    Sistema_de_Reservas --*  Sistema_de_Gestión_de_una_biblioteca
    class Sistema_de_Gestión_de_una_biblioteca{
      +lista usuarios
      +Catálogo catálogo
    }
    class Usuarios{
      +string id
      +string contraseña
      +lista notificaciones por sanciones
      +historial historial individual de préstamos
      +ver catálogo(catálogo)
      +acceder recurso online(catálogo)
      +prestar un libro(catálogo)
      +acceder al sistema de reservas()
    }
    class Administradores{
      +agregar un libro(catálogo)
      +remover un libro(catálogo)
      +procesar devolución(catálogo)
    }
    class Historial{
      +lista prestamos
    }
    class Prestamo{
      +Libro libros
      +string fecha de préstamos
      +string fecha de vencimiento
      +bool devuelto
      +lista sanciones
    }
    class Catálogo{
      +lista Libros
      +lista Recursos Online
    
    }
    class Libro{
      +string Título
      +string Autor
      +string Editorial
      +int edición
      +bool Disponibilidad
      +prestar a(usuarios)
    }
    class Recurso_Online{
      +string Tipo
      +string Título
      +string Autor
      +descargar(usuarios)
    }
    class Sistema_de_Prestamos{
      +historial historial general de préstamos
      +prohibir prestamos(usuarios)
    }
    class Sistema_de_Reservas{
      +ver salas()
    }
    class Sala{
      +bool disponibilidad
      +silla sillas
      +reservar sala()
    }
    class Sala_de_estudio{
      +mesa mesas de trabajo
    }
    class Sala_de_computadores{
      +computador computadores
    }
```

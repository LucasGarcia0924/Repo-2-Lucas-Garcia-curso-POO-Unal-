# Repo-2-Lucas-Garcia-curso-POO-Unal-
Solución a los ejercicios propuestos por el docente

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

Finalmente, al unir todas las clases se obtiene:

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

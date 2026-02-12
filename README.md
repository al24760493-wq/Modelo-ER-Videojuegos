# Modelo-ER-Videojuegos
Proyecto: Repositorio, Nombre: Brandon Gonzalez Ramirez, Proyecto: Arquitectura de Computadoras  Materia:Fundamentos de base de datos  Lenguaje/Herramientas: Java / GitHub  Fecha: Febrero 2026
# 🎮 Modelo Entidad-Relación - Sistema de Videojuegos

## 1. Título
Modelo Entidad-Relación para la Gestión de Videojuegos

## 2. Descripción
Este proyecto representa el diseño de una base de datos para un sistema de gestión de videojuegos. 
El modelo permite almacenar información sobre videojuegos, desarrolladores, plataformas y jugadores, 
así como las relaciones entre ellos.

## 3. Motivación
La industria de los videojuegos es una de las más importantes en el ámbito tecnológico. 
Este proyecto tiene como finalidad aplicar el modelo Entidad-Relación (E-R) para organizar 
de manera estructurada la información relacionada con videojuegos y demostrar la comprensión 
del diseño de bases de datos.

## 4. Diagrama Entidad-Relación (E-R)

Entidades:
- Videojuego (id_videojuego, nombre, genero, fecha_lanzamiento)
- Desarrollador (id_desarrollador, nombre, pais)
- Plataforma (id_plataforma, nombre, fabricante)
- Jugador (id_jugador, nombre_usuario, email)

Relaciones:
- Un desarrollador crea muchos videojuegos (1:N)
- Un videojuego puede estar en varias plataformas (N:M)
- Un jugador puede jugar muchos videojuegos (N:M)

## 5. Diagrama E-R en UML

Clases UML:

Clase Videojuego
- id_videojuego
- nombre
- genero
- fecha_lanzamiento

Clase Desarrollador
- id_desarrollador
- nombre
- pais

Clase Plataforma
- id_plataforma
- nombre
- fabricante

Clase Jugador
- id_jugador
- nombre_usuario
- email

Relaciones UML:
Desarrollador 1 ----- * Videojuego
Videojuego * ----- * Plataforma
Jugador * ----- * Videojuego

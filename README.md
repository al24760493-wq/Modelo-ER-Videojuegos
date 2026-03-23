🎮 Proyecto: Modelo-ER-Videojuegos
Repositorio: [Nombre del Repositorio en GitHub]

Nombre: Brandon Gonzalez Ramirez

Proyecto: Arquitectura de Computadoras

Materia: Fundamentos de Base de Datos

Lenguaje/Herramientas: Java / GitHub

Fecha: Febrero 2026

1. Título
Modelo Entidad-Relación para la Gestión de Videojuegos

2. Descripción
Este proyecto representa el diseño de una base de datos para un sistema de gestión de videojuegos. El modelo permite almacenar información sobre videojuegos, desarrolladores, plataformas y jugadores, así como las relaciones entre ellos. Se han actualizado los diagramas aplicando un proceso de normalización para asegurar la integridad de los datos.

3. Motivación
La industria de los videojuegos es una de las más importantes en el ámbito tecnológico. Este proyecto tiene como finalidad aplicar el modelo Entidad-Relación (E-R) para organizar de manera estructurada la información relacionada con videojuegos y demostrar la comprensión del diseño de bases de datos.

4. Diagrama Entidad-Relación (E-R) Normalizado
Para evitar redundancias, las relaciones N:M se han desglosado en tablas intermedias.

Entidades y Atributos:

Videojuego: (id_videojuego, nombre, genero, fecha_lanzamiento, id_desarrollador)

Desarrollador: (id_desarrollador, nombre, pais)

Plataforma: (id_plataforma, nombre, fabricante)

Jugador: (id_jugador, nombre_usuario, email)

Relaciones Actualizadas:

Un desarrollador crea muchos videojuegos (1:N).

Un videojuego puede estar en varias plataformas (N:M) -> Resuelto mediante tabla intermedia Videojuego_Plataforma.

Un jugador puede jugar muchos videojuegos (N:M) -> Resuelto mediante tabla intermedia Biblioteca.

5. Diagrama E-R en UML
Representación de clases para la implementación en Java:

Clase Desarrollador 1 ----- * Clase Videojuego

Clase Videojuego * ----- * Clase Plataforma (Asociación normalizada)

Clase Jugador * ----- * Clase Videojuego (Asociación normalizada)

6. Implementación de la Base de Datos (SQL)
Este script crea la estructura física basada en el diseño normalizado:
CREATE DATABASE Modelo_ER_Videojuegos;
USE Modelo_ER_Videojuegos;

-- Tabla Desarrollador
CREATE TABLE Desarrollador (
    id_desarrollador INT PRIMARY KEY AUTO_INCREMENT,
    nombre VARCHAR(100) NOT NULL,
    pais VARCHAR(50)
);

-- Tabla Videojuego (Incluye FK de Desarrollador)
CREATE TABLE Videojuego (
    id_videojuego INT PRIMARY KEY AUTO_INCREMENT,
    nombre VARCHAR(150) NOT NULL,
    genero VARCHAR(50),
    fecha_lanzamiento DATE,
    id_desarrollador INT,
    FOREIGN KEY (id_desarrollador) REFERENCES Desarrollador(id_desarrollador)
);

-- Tabla Plataforma
CREATE TABLE Plataforma (
    id_plataforma INT PRIMARY KEY AUTO_INCREMENT,
    nombre VARCHAR(50) NOT NULL,
    fabricante VARCHAR(50)
);

-- Tabla Jugador
CREATE TABLE Jugador (
    id_jugador INT PRIMARY KEY AUTO_INCREMENT,
    nombre_usuario VARCHAR(50) UNIQUE NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL
);

-- Tabla Intermedia: Videojuego_Plataforma (Normalización N:M)
CREATE TABLE Videojuego_Plataforma (
    id_videojuego INT,
    id_plataforma INT,
    PRIMARY KEY (id_videojuego, id_plataforma),
    FOREIGN KEY (id_videojuego) REFERENCES Videojuego(id_videojuego),
    FOREIGN KEY (id_plataforma) REFERENCES Plataforma(id_plataforma)
);

-- Tabla Intermedia: Biblioteca (Normalización N:M entre Jugador y Videojuego)
CREATE TABLE Biblioteca (
    id_jugador INT,
    id_videojuego INT,
    PRIMARY KEY (id_jugador, id_videojuego),
    FOREIGN KEY (id_jugador) REFERENCES Jugador(id_jugador),
    FOREIGN KEY (id_videojuego) REFERENCES Videojuego(id_videojuego)
);

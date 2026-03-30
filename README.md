# Sql2

Dataset para los datos del TP -- DATABASE CREATION
CREATE DATABASE IF NOT EXISTS logistica_n2;
USE logistica_n2;

-- TABLES
CREATE TABLE clientes (
    id_cliente INT PRIMARY KEY,
    nombre VARCHAR(50),
    direccion VARCHAR(100),
    telefono VARCHAR(20)
);

CREATE TABLE productos (
    id_producto INT PRIMARY KEY,
    descripcion VARCHAR(100),
    peso DECIMAL(10,2)
);

CREATE TABLE vehiculos (
    id_vehiculo INT PRIMARY KEY,
    patente VARCHAR(20),
    capacidad DECIMAL(10,2)
);

CREATE TABLE envios (
    id_envio INT PRIMARY KEY,
    id_cliente INT,
    id_producto INT,
    id_vehiculo INT,
    fecha_entrega DATE,
    costo DECIMAL(10,2),
    FOREIGN KEY (id_cliente) REFERENCES clientes(id_cliente),
    FOREIGN KEY (id_producto) REFERENCES productos(id_producto),
    FOREIGN KEY (id_vehiculo) REFERENCES vehiculos(id_vehiculo)
);

Script de Insertar registros

-- INSERT 
-- CLIENTES: 
INSERT INTO clientes VALUES
(1, 'Ana Perez', 'Calle Falsa 123', '12345'),
(2, 'Carlos Gomez', 'Av. Central 555', 'NULL'), 
(3, 'Carlos Gomez', 'Av. Central 555', '48922'); 

-- PRODUCTOS: 
INSERT INTO productos VALUES
(1, 'Caja pequeña', 2.50),
(2, 'Paquete mediano', -1.00), 
(3, 'Bulto grande', NULL); 

-- VEHICULOS: 
INSERT INTO vehiculos VALUES
(1, 'AA123BB', 500.00),
(2, 'CC456DD', NULL), 
(3, 'AA123BB', 600.00); 

-- ENVIOS: 
INSERT INTO envios VALUES
(1, 1, 1, 1, '2023-05-01', 1500.00),
(2, 3, 1, 1, '2023-05-02', 1200.00), 
(3, 2, 2, 1, '2023-06-01', 1300.00);


Script de Insertar registros adicionales

USE logistica_n2;


-- CLIENTES adicionales
INSERT INTO clientes VALUES
(4, 'Laura Martinez', 'San Martin 100', '4556677'),
(5, 'Pedro Ruiz', 'Belgrano 220', 'NULL'), 
(6, 'Laura Martinez', 'San Martin 100', '4556677'),
(7, 'Mariana Diaz', 'Calle 7 n 1230', '221546789'),
(8, 'Enzo Fernandez', 'San Martin 320', '115313456'),
(9, 'Julian Alvarez', 'Calchin 10 Cordoba', '3515221278'),
(10, 'Lionel Messi', 'Boulevard 27 de Febrero Rosario', '3415345799'); 

-- PRODUCTOS adicionales
INSERT INTO productos VALUES
(4, 'Sobres documentacion', 0.50),
(5, 'Caja herramientas', 8.00),
(6, 'Equipo pesado', -15.00),
(7, 'Caja de Guardado Mediana', 1.40),
(8, 'Caja de Guardado Grande', 2.00),
(9, 'Caja Mudanza', 1.00),
(10,'Canasto Plastico', 0.80); 

-- VEHICULOS adicionales
INSERT INTO vehiculos VALUES
(4, 'DD789EE', 1200.00),
(5, 'EE111FF', -300.00), 
(6, 'CC456DD', 800.00); 

-- ENVIOS adicionales
INSERT INTO envios VALUES
(7, 4, 4, 4, '2023-05-10', 900.00),
(8, 5, 5, 4, '2023-05-11', 1100.00),
(9, 6, 6, 5, '2023-05-12', 0.00), 
(10, 3, 4, 4, '2023-05-13', 700.00), 
(11, 4, 5, 4, '2023-05-14', 500.00), 
(12, 4, 4, 2, '2023-05-15', 600.00), 
(13, 5, 5, 5, '2032-01-01', 1300.00),
(14, 2, 4, 1, '2023-08-10', -900.00);


3. Deteccion de incosistencias lógicas o Valores Invalidos: Identificar envios 
con información valores indebidos,o valores erróneos. Con que consulta SQL 
los identifico? 
4. Analizar la información para obtener:
a) Total de envíos por mes 
b) Costo total de envíos por mes
c) Costo promedio por vehículo
d) Total clientes con envíos
e) Cantidad de envíos por producto (visualizar el nombre del producto)
f) Clientes con más de un envío (mostrar el nombre del cliente)
PARTE 3 – Controles de Auditoría 
1. Utilizando un LEFT JOIN,o RIGHT JOIN obtener el listado de clientes que no 
tienen envíos asociados.
 id_cliente
 nombre
 dirección
2. Mostrar todos los productos, incluyendo aquellos que no aparecen en ningún 
envío.
 id_producto
 descripción
 id_envio (si existe)

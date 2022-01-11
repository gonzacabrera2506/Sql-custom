# Sql inicial

# TEMA 1- MANIPULACION

CREATE TABLE curso (
  id INT AUTO_INCREMENT NOT NULL,
  nombre VARCHAR(30) NOT NULL,
  descripcion VARCHAR(50),
  turno VARCHAR(50) NOT NULL,
  PRIMARY KEY(id)
);
ALTER TABLE curso ADD cupo INT;

INSERT INTO curso (id,nombre, descripcion, turno, cupo) VALUES (101,'Algoritmos','Algoritmos Y Estructuras De Datos','Mañana',35);

INSERT INTO curso (id, nombre, descripcion, turno, cupo) VALUES (105, '','','Tarde',30);

INSERT INTO curso (id, nombre, descripcion, turno, cupo) VALUES (102, 'Matemática Discreta','','Tarde',30);

UPDATE curso SET cupo = 25;

DELETE FROM curso WHERE nombre = 'Algoritmos';

# TEMA 3- QUERIES

SELECT nombre, apellido, fecha_nacimiento FROM profesor ORDER BY fecha_nacimiento ASC;

SELECT nombre, apellido FROM profesor WHERE salario >= 65000;

SELECT nombre, apellido FROM profesor WHERE fecha_nacimiento BETWEEN 1980-01-01 AND 1989-12-31;

SELECT nombre, apellido FROM profesor LIMIT 5;

SELECT nombre, apellido FROM profesor WHERE apellido LIKE 'P%';

SELECT nombre, apellido FROM profesor WHERE fecha_nacimiento BETWEEN 1980-01-01 AND 1989-12-31 AND salario > 80000;

# Sql intermedio

# TEMA 1- FUNCIONES AGREGADAS
1-Escriba una consulta para saber cuántos estudiantes son de la carrera Mecánica.
SELECT COUNT(ESTUDIANTE_legajo) from inscripcion WHERE carrera = 'Mecánica';

2- Escriba una consulta para saber, de la tabla PROFESOR, el salario mínimo de los profesores nacidos en la década del 80.
SELECT MIN(salario) FROM profesor WHERE fecha_nacimiento BETWEEN  '1980-01-01' AND '1989-12-31';

3-Escriba las siguientes consultas:

Cantidad de pasajeros por país
SELECT pais.nombre, COUNT(*) FROM pasajero JOIN pais ON pasajero.idpais = pais.idpais
GROUP BY pais.nombre

Suma de todos los pagos realizados
SELECT SUM(monto) FROM pago;

Suma de todos los pagos que realizó un pasajero. El monto debe aparecer con dos decimales.
SELECT idpasajero, ROUND(SUM(monto), 2) FROM pago GROUP BY idpasajero;

Promedio de los pagos que realizó un pasajero.
SELECT idpasajero, AVG(SUM(monto) FROM pago GROUP BY idpasajero;











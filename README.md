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

SELECT pais.nombre, COUNT(*) FROM pasajero JOIN pais ON pasajero.idpais = pais.idpais GROUP BY pais.nombre;

Suma de todos los pagos realizados

SELECT SUM(monto) FROM pago;

Suma de todos los pagos que realizó un pasajero. El monto debe aparecer con dos decimales.

SELECT idpasajero, ROUND(SUM(monto), 2) FROM pago GROUP BY idpasajero;

Promedio de los pagos que realizó un pasajero.

SELECT idpasajero, AVG(SUM(monto) FROM pago GROUP BY idpasajero;

# TEMA 2- MULTIPLE TABLES

1-Nombre, apellido y cursos que realiza cada estudiante.

SELECT estudiante.nombre, estudiante.apellido, curso.nombre FROM inscripcion JOIN curso ON inscripcion.curso_codigo = curso.codigo JOIN estudiante ON inscripcion.estudiante_legajo = estudiante.legajo;

2-Nombre, apellido y cursos que realiza cada estudiante, ordenados por el nombre del curso.

SELECT estudiante.nombre, estudiante.apellido, curso.nombre FROM inscripcion JOIN curso ON inscripcion.curso_codigo = curso.codigo JOIN estudiante ON inscripcion.estudiante_legajo = estudiante.legajo ORDER BY curso.nombre ASC;

3-Nombre, apellido y cursos que dicta cada profesor.

SELECT profesor.nombre, profesor.apellido, curso.nombre FROM profesor LEFT JOIN curso ON profesor.id = curso.profesor_id;

4-Nombre, apellido y cursos que dicta cada profesor, ordenados por el nombre del curso.

SELECT profesor.nombre, profesor.apellido, curso.nombre FROM profesor LEFT JOIN curso ON profesor.id = curso.profesor_id ORDER BY curso.nombre ASC;

5-Cupo disponible para cada curso (Si el cupo es de 35 estudiantes y hay 5 inscriptos, el cupo disponible será 30).

SELECT curso.nombre, curso.cupo, curso.cupo - COUNT(inscripcion.numero) AS 'DISPONIBLE' FROM inscripcion RIGHT JOIN curso ON inscripcion.curso_codigo = curso.codigo GROUP BY curso.nombre, curso.cupo

6-Cursos cuyo cupo disponible sea menor a 10.

SELECT curso.nombre, curso.cupo, curso.cupo - COUNT(inscripcion.numero) AS 'DISPONIBLE MENOR A 10'
FROM inscripcion RIGHT JOIN curso ON inscripcion.curso_codigo = curso.codigo GROUP BY curso.nombre, curso.cupo HAVING curso.cupo - COUNT(inscripcion.numero) < 10

# TEMA 3- INDICES

CREATE TABLE persona(
  id INT NOT NULL,
  nombre VARCHAR(50) NOT NULL
);

INSERT INTO persona VALUES
(4, 'juan'),
(2, 'camilo'),
(1, 'gonzalo'),
(3, 'lucio');

SELECT * FROM persona;

ALTER TABLE persona
ADD PRIMARY KEY (id);

SELECT * FROM persona;



# TEMA 4- QUERIES ANIDADAS

1-Escriba una consulta que devuelva la cantidad de profesores que dictan más de un curso en el turno Noche.

SELECT COUNT(*) FROM profesor WHERE id IN (SELECT DISTINCT profesor_id FROM curso WHERE turno like 'Noche');

2-Escriba una consulta para obtener la información de todos los estudiantes que no realizan el curso con código 105.

SELECT * FROM estudiante WHERE legajo NOT IN (SELECT estudiante_legajo FROM inscripcion WHERE curso_codigo = 105);



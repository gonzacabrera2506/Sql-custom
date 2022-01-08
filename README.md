# Sql-custom

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


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

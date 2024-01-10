# Crecion de tablas con Sqlite 3

### Tabla Profesores 
``` sql
CREATE TABLE profesores (
    ID INTEGER NOT NULL PRIMARY KEY AUTOINCREMENT,
    Apellidos TEXT NOT NULL,
    Nombre TEXT NOT NULL,
    DNI TEXT NULL,
    Es_Tutor TEXT NOT NULL );

INSERT INTO comments ( ID, Apellidos, Nombre, DNI, Es_Tutor )
VALUES ( '1', 'Doe',
'Olivia', '47281935O.', 'no' );
```
Y gracias al comando INSERT, introduciremos los datos correspondientes a cada fila
```

+----+-----------+--------+------------+----------+
| ID | Apellidos | Nombre |    DNI     | Es_Tutor |
+----+-----------+--------+------------+----------+
| 1  | Doe       | Olivia | 47281935O. | no       |
| 2  | Jones     | Mason  | 91456728P  | si       |
| 3  | Wilson    | Lian   | 13645876L  | no       |
| 4  | Taylor    | Ava    | 30587246U  | no       |
| 5  | Jackson   | Ethan  | 89665460   | si       |
+----+-----------+--------+------------+----------+
```


### Tabla Tiene 

```sql
create table tiene(
ID_Profesores  integer  references Direccion,
        DNI_Estudiante text references Estudiante
);

INSERT INTO comments ( DNI_Estudiante, ID_Profesores )
VALUES ( '23467664H', '1' );
```
Y con el comando insert introducimos el resto de datos
```
+-------------+----------------+
| ID_Profesor | DNI_Estudiante |
+-------------+----------------+
| 1           | 23467664H      |
| 2           | 576456321J     |
| 3           | 87654321B      |
| 4           | 53290736T      |
| 5           | 78654901K      |
+-------------+----------------+
```
### Tabla Estudiantes
```
CREATE TABLE Estudiantes (
    DNI_Estudiante TEXT NOT NULL PRIMARY KEY,
    Nombre_Estudiante TEXT NOT NULL,
    Apellidos_Estudiante TEXT NOT NULL);

INSERT INTO comments ( DNI_Estudiante, Nombre_Estudiante, Apellidos_Estudiante )
VALUES ( '23467664H', 'John', 'Dou' );
```
Con el insert introducimos los datos restantes
```
+----------------+-------------------+----------------------+
| DNI_Estudiante | Nombre_Estudiante | Apellidos_Estudiante |
+----------------+-------------------+----------------------+
| 23467664H      | John              | Dou                  |
| 576456321J     | Emily             | Lee                  |
| 87654321B      | Chris             | La                   |
| 53290736T      | Michael           | Bradley              |
| 78654901K      | Sarah             | Tranv                |
+----------------+-------------------+----------------------+
```

# Creación de tablas con Sqlite 3.

### Creamos la tabla Profesores utilizando el comando CREATE TABLE
#### Colocamos NOT NULL en todas las tablas ya que no hay un apartado en la table que este vacio.  

``` sql
CREATE TABLE profesores (
    ID INTEGER NOT NULL PRIMARY KEY AUTOINCREMENT,
    Apellidos TEXT NOT NULL,
    Nombre TEXT NOT NULL,
    DNI TEXT NULL,
    Es_Tutor TEXT NOT NULL );
```
### Y gracias al comando INSERT, introduciremos los datos correspondientes a cada fila.
```sql
INSERT INTO comments ( ID, Apellidos, Nombre, DNI, Es_Tutor )
VALUES ( '1', 'Doe',
'Olivia', '47281935O.', 'no' );

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


### Creación de la Tabla Tiene .

```sql
create table tiene(
ID_Profesores  integer  references Direccion,
        DNI_Estudiante text references Estudiante
);
```
### Y con el comando insert introducimos el resto de datos.
```sql
INSERT INTO comments ( DNI_Estudiante, ID_Profesores )
VALUES ( '23467664H', '1' );

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
### Creación de la tabla Estudiantes.
```sql
CREATE TABLE Estudiantes (
    DNI_Estudiante TEXT NOT NULL PRIMARY KEY,
    Nombre_Estudiante TEXT NOT NULL,
    Apellidos_Estudiante TEXT NOT NULL);
```
### Con el insert introducimos los datos restantes.
```sql
INSERT INTO comments ( DNI_Estudiante, Nombre_Estudiante, Apellidos_Estudiante )
VALUES ( '23467664H', 'John', 'Dou' );

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

### Creación de tabla pertenece.
```sql
create table pertenece(
ID_Email  text	references Email(ID),
	DNI_Estudiante text references Estudiante(DNI)
);
```
### Con el insert introducimos los datos restantes.
```sql
Insert into pertenece (ID_email,DNI_Estudiante ) values(687,'23467664H');

+----------+----------------+
| ID_Email | DNI_Estudiante |
+----------+----------------+
| 152      | 23467664H      |
| 687      | 23467664H      |
| 466      | 576456321J     |
| 5483     | 576456321J     |
| 186      | 576456321J     |
| 153      | 8765321B       |
| 6883     | 53290736T      |
| 3889     | 78654901K      |
+----------+----------------+
```
### Creación de tabla email.
```sql
create table email (
	ID  integer NOT NULL PRIMARY KEY,
	email text NOT NULL
 );
```
### Con el insert introducimos los datos restantes.
```sql
Insert into email (ID,email) values(152,’john.doe@example.com’);
Insert into email (ID,email) values(687,’alex.jones@yahoo.com’);
Insert into email (ID,email) values(466,’emily.smith@gmail.com’);
+------+--------------------------+
|  ID  |          email           |
+------+--------------------------+
| 152  | john.doe@example.com     |
| 153  | chris.wilson@outlook.com |
| 186  | lia.mer@hotmail.com      |
| 466  | emily.smith@gmail.com    |
| 687  | alex.jones@yahoo.com     |
| 3889 | saraha.jackson@yahoo.com |
| 5483 | lisa.miller@hotmail.com  |
| 6883 | micheal.taylor@gmail.com |
+------+--------------------------+
```

### Crecion de tabla posee.
```sql
create table posee(
ID_Direccion  integer	references Direccion(ID),
	DNI_Estudiante text references Estudiante(DNI)
);
```
### Con el insert introducimos los datos restantes
```sql
Insert into posee (ID_Direccion, DNI_Estudiante) values(99, ‘23367664H’);
Insert into posee (ID_Direccion, DNI_Estudiante) values(12,78654901K);
+--------------+----------------+
| ID_Direccion | DNI_Estudiante |
+--------------+----------------+
| 99           | 23367664H      |
| 97           | 576456321J     |
| 34           | 8765321B       |
| 65           | 53290736T      |
| 12           | 78654901K      |
+--------------+----------------+
```
### Creación de tabla Direccion.
```sql
create table Direccion (
	ID  integer NOT NULL PRIMARY KEY,
	Provincia text NOT NULL,
	Numero integer NOT NULL,
	Codigo_Postal integer NOT NULL,
	Piso integer NOT NULL,
	Calle text NOT NULL,
	Municipio text NOT NULL
 );
```
### Con el insert introducimos los datos restantes.
```sql
insert into Direccion (ID, Provincia, Numero, Codigo_Postal, Piso, Calle, Municipio) values(99, 'USA', 123, 441211, 1, 'Main Street', 'Springfield');

insert into Direccion (ID, Provincia, Numero, Codigo_Postal, Piso, Calle, Municipio) values(97, 'Canada', 456, 00177, 9, 'Oak Avenue', 'Willowville');
+----+---------------+--------+---------------+------+-------------+--------------+
| ID |   Provincia   | Numero | Codigo_Postal | Piso |    Calle    |  Municipio   |
+----+---------------+--------+---------------+------+-------------+--------------+
| 12 | Nueva Zelanda | 234    | 44766         | 1    | Maple Drive | Mountainview |
| 34 | Australia     | 789    | 99122         | 9    | Pine Lane   | Meadows Town |
| 65 | Reino Unido   | 101    | 22155         | 7    | Elm         | Lakeside     |
| 97 | Canada        | 456    | 177           | 9    | Oak Avenue  | Willowville  |
| 99 | USA           | 123    | 441211        | 1    | Main Street | Springfield  |
+----+---------------+--------+---------------+------+-------------+--------------+
```
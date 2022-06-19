# MacheteMYSQL

Machete para aprender y recordar cosas fundamentales de MYSQL.

## Crear una base de datos en MYSQL
Para crear una base de datos en MYSQL debemos escribir
```
**create database** nombredelabase;
```
-Es muy importante poner punto y coma al final de cada linea de codigo ";"

Luego para saber si nuestra base de datos se creeo correctamente debemos esribir la siguiente linea de codigo
```
**show databases;**
```

Para decirle a mysql que use nuestra base para empezar a hacer todo nuestro trabajo, se debe poner
el codigo "use" seguido del nombre que le pusimos a nuestra base en el primer paso.
```
**use** nombredelabase;
```

### Crear nuestra primera tabla
Para empezar a construir la tabla, debemos poner el comando CREATE TABLE seguido del nombre que le queramos poner a la tabla, este comando tiene que ir con mayusculas.
Ejemplo:
```
CREATE TABLE animales ();
```
Dentro de los corchetes (), es donde vamos a construir nuestra tabla.
```
CREATE TABLE animales (
    id **int**,
    tipo **varchar** (255),
    estado **varchar** (255),
    **PRIMARY KEY** (id)
);
```
-**int** : se refiere a un numero entero, en este ejemplo la primera fila que seria "id" seria un numero de tipo entero.
-**varchar**: varchar se refiere a que esa columna va a ser de tipo caracter y con el numero dentro de los parantesis es hasta cuantos caractares hay permitido.
-**estad**: es de tipo carcarter tambien
-**PRIMARY KEY**: Con este comando estamos diciendo que la llave primara es la columna "id", es decir esta primary key es unica y no se puede repetir.


## Como agregar registros o valores a nuestra tabla?
Cuando queramos agregar estos registros o valores a nuestra tabla tenemos que usar el siguiente codigo o comando:
```
**INSERT INTO** animales (tipo, estado) **VALUES** ('Perro', 'Feliz')
```

Basicamente lo que dice la anterior linea de codigo es
Inserta en mi tabla animales (nombrecolumna1, nombrecolumna2) el valor ('valorparacolumna1', 'valorparacolumna2')
En el ejemplo anterior estaria insertando en mi tabla animales en las columnas especificadas los valores perro feliz y cuando consulte por la tabla, estos valores o cambios nuevos que realize se van a ver reflejados en la misma.

**PERO ESTO VA A TIRAR UN ERROR**, Esto se debe a que nuestra **PRIMARY KEY** no aumenta automaticamente, es decir. Cuando nosotros creamos nuestra tabla tenemos que poner una primary key para que esta sea un identificador unico de los datos, en este ejemplo yo puse como Primary Key a la columna "id", esta debe aumentar cada vez que yo agregue nuevos valores o registro a la tabla.
EJEMPLO: de como tendria que ir aumentando en caso de que yo agregase el valor tipo 'Gato' con su estado 'Triste'
id  Tipo    Estado
1   Perro   Feliz
2   Gato    Triste

## Aumentar el id automaticamente
Para resolver el problema anterior y que no nos tire error tenemos que hacer que nuestro id o PRIMARY KEY aumente su valor automaticamente cada vez que agreguemos nuevos registros hay que usar el siguiente comando o linea de codigo.
```
ALTER TABLE animales MODIFY COLUMN id **int** auto_increment;
```
Lo que dice es, Altera la tabla animales y Modifica La columna "id" int auto_increment; el int debe ir si o si para que sea un numero entero y auto_increment para que cada vez que se aumente la tabla vaya generando un numero entero en id automaticamente.


## Copiar el error y mejorarlo?
Para ver y copiar el error de nuestra tabla ponemos el comando
```
SHOW CREATE TABLE animales;
```
Copiamos con Copy Field y pegamos en el editor, sacamos las comillas y lo ejecutamos, podemos ir agregando nuevos registros si queremos.


## Como listar todos los registros que ingresamos
La cosulta que nosotros debemos usar es **SELECT** este nos permite seleccionar elementos que se encuentran dentro de una tabla
como segundo argumento debemos indicar lo siguiente:
```
SELECT * FROM animales;
```
Esto selecciona toda la tabla, es decir vamos a ver todo lo que contiene.
Si queremos seleccionar una columna de nuestra tabla podemos hacerlo de la siguiente forma
```
SELECT * FROM animales WHERE id = 1;
```
Esto es. Selecciona todo lo que este en la tabla animales DONDE el id sea igual a 1
```
SELECT * FROM animales WHERE estado = 'Feliz';
```
En este caso puede ser que la tabla devuelma mas de un registro, por que otros registros pueden tener el estado de 'Feliz'

Tambien podes agregar otra condicion a nuestra busqueda, con el operador AND. de la siguiente manera-
```
SELECT * FROM animales WHERE estado = 'Feliz' AND tipo = 'Perro';
```
Esto va a cruzar los dos datos, para ver que registro corresponde con esas dos condiciones.


## Como actualizar los registros que ya se encuentran en nuestra Base de Datos
```
UPDATE animales SET estado = 'Feliz' where id = 2;
```
Aca lo que decimos es que mediante UPDATE queremos actualizar dentro de nuesta tabla animales la columna de estado y queres que pase a ser feliz, pero solamente esto donde exista un registro que contenga el id de 3.

## DELETE
Cuando nostros queramos relizar un delete a nuestras tablas o realizar un update, tenemos que indicar necesariamente un id,
si no indicamos el id, nos va a tirar un error.
```
DELETE from animales where id = 2;
```
Esto elimina de nuestra tabla animales donde el id sea 2;


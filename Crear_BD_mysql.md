# Comandos Mysql

## Conectar a servidor MySql

```mysql
mysql -h host_de_tu_base_de_datos -P 3306 -u nombre_de_usuario -p
```
## Ver las base de datos que hay en este servidor

```mysql
mysql> SHOW databases;
```

## Crear Base de datos

Con compatibilidad UTF8
```mysql
create database MiBaseDeDatos character set utf8;
```

## Crear Usuario

Para host localhost
```mysql
create user nombre_de_usuario@'localhost';
```
Para cualquier host
```mysql
create user nombre_de_usuario@'%';
```

## Poner password a un usuario

```mysql
set password for 'nombre_de_usuario'@'%' = PASSWORD('M1Sup3rP4ssw0rd;');
```

## Dar permisos al nuevo usuario en nuestra base de datos

```mysql
grant all on MiBaseDeDatos.* to 'nombre_de_usuario'@'localhost' ;
```

## Reiniciamos la cache y todo lo necesario para que se otorgen los permisos

```mysql
flush privileges;
```

## Ver los usuarios que tenemos en nuestra base de datos

```mysql
SELECT user FROM mysql.user;
```
Que nos muestre también a que host pernece el usuario

```mysql
SELECT user,host FROM mysql.user;
```

## Ver permisos del usuario

```mysql
SHOW GRANTS FOR 'nombre_de_usuario'@'localhost';
```

## Cambiarnos a la base de datos

```mysql
mysql> USE MiBaseDeDatos;
```

## Ver tablas de la base de datos

```mysql
mysql> SHOW Tables;
```
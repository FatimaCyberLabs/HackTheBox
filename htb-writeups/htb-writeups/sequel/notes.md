# Sequel — Starting Point (Tier 1)

**Dificultad:** Very Easy · **SO:** Linux · **Categoría:** Bases de datos mal aseguradas

## Resumen
Introducción a bases de datos MySQL accesibles con credenciales débiles o por defecto, y a la enumeración de su contenido.

## Herramientas utilizadas
- `nmap`
- `mysql` (cliente de línea de comandos)

## Metodología

**1. Reconocimiento**
```bash
nmap -sV -p- <IP>
```
Puerto 3306/tcp abierto — **MySQL**.

**2. Acceso**
```bash
mysql -h <IP> -u root -p
```
Conexión con credenciales por defecto o débiles (usuario `root` sin contraseña o con una contraseña trivial).

**3. Enumeración**
```sql
SHOW DATABASES;
USE <base_de_datos>;
SHOW TABLES;
SELECT * FROM <tabla>;
```
Exploración de las bases de datos disponibles hasta localizar información relevante.

**4. Flag**
Extraída de una tabla dentro de la base de datos.

## Habilidades demostradas
- Conexión y enumeración de servidores MySQL
- Uso de consultas SQL básicas para explorar esquemas y tablas
- Reconocimiento de credenciales por defecto como vector de acceso

## Aprendizaje
Refuerza la importancia de credenciales fuertes y de restringir el acceso remoto en servicios de bases de datos expuestos — un fallo de configuración muy habitual en entornos de desarrollo y producción.

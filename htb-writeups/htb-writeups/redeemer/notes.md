# Redeemer — Starting Point (Tier 0)

**Dificultad:** Very Easy · **SO:** Linux · **Categoría:** Bases de datos expuestas

## Resumen
Introducción a Redis, una base de datos en memoria clave-valor, y a la falta de autenticación como vector de acceso directo a los datos almacenados.

## Herramientas utilizadas
- `nmap`
- `redis-cli`

## Metodología

**1. Reconocimiento**
```bash
nmap -sV -p- <IP>
```
Puerto de Redis abierto (por defecto 6379/tcp).

**2. Conexión**
```bash
redis-cli -h <IP>
```
Conexión directa sin necesidad de credenciales.

**3. Enumeración**
```
INFO
```
Obtención de la versión del servidor y estadísticas generales (memoria, clientes conectados, uptime).

**4. Exploración de datos**
```
KEYS *
GET <clave>
```
Listado de claves almacenadas y extracción de su contenido.

**5. Flag**
Localizada entre los valores almacenados en la base de datos.

## Habilidades demostradas
- Interacción con bases de datos NoSQL mediante línea de comandos
- Enumeración de servidores sin autenticación
- Extracción de datos sensibles desde estructuras clave-valor

## Aprendizaje
Redis sin autenticación configurada es un fallo de seguridad grave y sorprendentemente común en despliegues reales, especialmente en entornos de desarrollo expuestos por error a internet.

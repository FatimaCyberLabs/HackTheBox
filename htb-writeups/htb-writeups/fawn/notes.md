# Fawn — Starting Point (Tier 0)

**Dificultad:** Very Easy · **SO:** Linux · **Categoría:** Servicios inseguros por defecto

## Resumen
Introducción al protocolo FTP y a un fallo de configuración muy común: acceso anónimo habilitado, que permite a cualquiera listar y descargar archivos sin credenciales reales.

## Herramientas utilizadas
- `nmap`
- `ftp`

## Metodología

**1. Reconocimiento**
```bash
nmap -sV -p- <IP>
```
Puerto 21/tcp abierto — **FTP**.

**2. Acceso**
```bash
ftp <IP>
```
Usuario: `anonymous` · Contraseña: en blanco (o cualquier valor, a veces se pide un email cualquiera).

**3. Enumeración**
```
ls
```
Listado de archivos disponibles en el servidor FTP.

**4. Descarga**
```
get <archivo>
```
Descarga del archivo relevante al directorio local para su análisis.

**5. Flag**
Contenida en el archivo descargado, revisado con `cat`.

## Habilidades demostradas
- Identificación de servicios FTP mediante escaneo de puertos
- Uso del cliente FTP en modo interactivo
- Reconocimiento de acceso anónimo como vector de exfiltración de datos

## Aprendizaje
El FTP anónimo es una mala práctica muy común en entornos reales mal configurados — un ejemplo claro de cómo un servicio "de confianza" puede convertirse en un vector de fuga de información si no se restringe el acceso.

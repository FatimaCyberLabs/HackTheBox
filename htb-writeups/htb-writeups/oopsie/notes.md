# Oopsie — Starting Point (Tier 2)

**Dificultad:** Very Easy · **SO:** Linux · **Categoría:** Control de acceso roto + escalada de privilegios

## Resumen
Explotación de una aplicación web con control de acceso mal implementado (manipulación de rol de usuario), seguida de escalada de privilegios mediante un binario con capacidades especiales.

## Herramientas utilizadas
- `nmap`
- Navegador web / Burp Suite (para modificar cookies/parámetros)
- Web shell básica
- `find` (búsqueda de binarios con capabilities/SUID)

## Metodología

**1. Reconocimiento**
```bash
nmap -sV -p- <IP>
```
Servicio web identificado.

**2. Enumeración web**
Descubrimiento de una función de subida de archivos accesible manipulando una cookie o parámetro que determina el rol del usuario (ej. `role=guest` → `role=admin`).

**3. Acceso inicial**
Subida de un archivo malicioso (web shell) aprovechando el acceso elevado obtenido, para ejecutar comandos en el servidor → **flag de usuario**.

**4. Escalada de privilegios**
```bash
find / -perm -4000 2>/dev/null
getcap -r / 2>/dev/null
```
Identificación de un binario con permisos especiales (SUID o capabilities) mal configurado que permite escalar a root → **flag de root**.

## Habilidades demostradas
- Explotación de control de acceso roto (Broken Access Control, OWASP Top 10)
- Subida y ejecución de web shells
- Enumeración de binarios SUID/capabilities para escalada de privilegios en Linux

## Aprendizaje
Ejemplo clásico de control de acceso roto combinado con mala configuración de permisos a nivel de sistema — dos de los fallos más recurrentes tanto en aplicaciones web como en hardening de servidores Linux.

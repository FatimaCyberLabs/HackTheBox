# Appointment — Starting Point (Tier 1)

**Dificultad:** Very Easy · **SO:** Linux · **Categoría:** SQL Injection

## Resumen
Primera máquina de Tier 1: introduce una vulnerabilidad web clásica, SQL Injection, en un formulario de login.

## Herramientas utilizadas
- `nmap`
- Navegador web (Burp Suite opcional para interceptar peticiones)

## Metodología

**1. Reconocimiento**
```bash
nmap -sV -p- <IP>
```
Servicio web (HTTP) identificado.

**2. Enumeración**
Inspección de la aplicación web: un formulario de inicio de sesión simple, sin protecciones visibles de sanitización de entrada.

**3. Explotación**
Bypass de autenticación mediante SQL Injection básica en el campo de usuario/contraseña, del tipo:
```
' OR '1'='1
```
Esto manipula la consulta SQL subyacente para que la condición de autenticación se cumpla siempre.

**4. Flag**
Obtenida tras saltarse el login y acceder al panel protegido.

## Habilidades demostradas
- Identificación de formularios vulnerables a inyección
- Comprensión básica de cómo se construyen las consultas SQL en el backend
- Primer bypass de autenticación web

## Aprendizaje
Primer contacto real con explotación web: cómo una validación de entrada insuficiente permite manipular una consulta SQL para evadir la autenticación, una de las vulnerabilidades más históricas y recurrentes del OWASP Top 10.

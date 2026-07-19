# Crocodile — Starting Point (Tier 1)

**Dificultad:** Very Easy · **SO:** Linux · **Categoría:** Encadenamiento de servicios

## Resumen
Combina enumeración de FTP anónimo con enumeración web para encontrar credenciales válidas y acceder a un panel protegido — un buen ejemplo de cómo un hallazgo en un servicio puede comprometer otro.

## Herramientas utilizadas
- `nmap`
- `ftp`
- Navegador web

## Metodología

**1. Reconocimiento**
```bash
nmap -sV -p- <IP>
```
Puertos FTP (21) y HTTP (80) abiertos.

**2. Enumeración FTP**
```bash
ftp <IP>
```
Acceso anónimo revela un archivo con credenciales (usuario/contraseña) en texto plano.

**3. Enumeración web**
Localización de un panel de login en el servicio HTTP.

**4. Acceso**
Uso de las credenciales encontradas en el FTP para autenticarse en el panel de administración web.

**5. Flag**
Localizada tras el acceso autenticado al panel.

## Habilidades demostradas
- Correlación de hallazgos entre distintos servicios de una misma máquina
- Enumeración FTP orientada a la búsqueda de credenciales
- Reutilización de credenciales encontradas para pivotar entre servicios

## Aprendizaje
Ejemplo claro de cómo encadenar hallazgos entre distintos servicios (FTP → Web) para lograr acceso: la enumeración de un servicio puede dar la clave para comprometer otro completamente distinto.

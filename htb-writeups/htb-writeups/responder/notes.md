# Responder — Starting Point (Tier 1)

**Dificultad:** Very Easy · **SO:** Windows · **Categoría:** Captura y crackeo de credenciales

## Resumen
Introducción al ataque de captura y crackeo de hashes NTLM en entornos Windows, usando la herramienta Responder para interceptar autenticaciones de red.

## Herramientas utilizadas
- `nmap`
- `Responder`
- `hashcat` / `john`

## Metodología

**1. Reconocimiento**
```bash
nmap -sV -p- <IP>
```
Servicios típicos de Windows identificados (SMB, HTTP).

**2. Captura de hash**
```bash
sudo responder -I <interfaz>
```
Se fuerza al sistema objetivo a intentar autenticarse contra la máquina atacante (por ejemplo, mediante una ruta UNC mal resuelta), lo que permite interceptar un hash **NTLMv2**.

**3. Crackeo offline**
```bash
hashcat -m 5600 hash.txt rockyou.txt
```
Uso de un diccionario de contraseñas comunes para crackear el hash capturado sin necesidad de fuerza bruta online.

**4. Acceso**
Uso de las credenciales obtenidas para autenticarse en un servicio del sistema (SMB o similar).

## Habilidades demostradas
- Configuración y uso de Responder para captura de tráfico de autenticación
- Comprensión del protocolo NTLM y sus debilidades
- Crackeo de hashes offline con herramientas estándar del sector

## Aprendizaje
Primer contacto con ataques de captura de credenciales en entornos Active Directory/Windows — una técnica muy relevante en pentesting real de redes corporativas, y una de las más citadas en informes de intrusión.

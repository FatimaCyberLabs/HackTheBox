# Meow — Starting Point (Tier 0)

**Dificultad:** Very Easy · **SO:** Linux · **Categoría:** Servicios inseguros por defecto

## Resumen
Primera máquina de HTB, pensada para introducir la conexión básica a un servicio de red inseguro y familiarizar con el flujo estándar: escanear → identificar servicio → conectarse → capturar flag.

## Herramientas utilizadas
- `nmap`
- `telnet`

## Metodología

**1. Reconocimiento**
```bash
nmap -sV -p- <IP>
```
Escaneo completo de todos los puertos para identificar servicios activos.

**2. Servicio identificado**
Puerto 23/tcp abierto — **Telnet**, protocolo antiguo que transmite todo (incluidas credenciales) sin cifrar.

**3. Acceso**
```bash
telnet <IP>
```
El servicio permitía login como usuario `root` con contraseña en blanco — una mala configuración de seguridad clásica que no debería darse en ningún sistema real.

**4. Flag**
Localizada en el directorio home del usuario tras el login (`ls -la` + `cat`).

## Habilidades demostradas
- Escaneo de puertos con Nmap
- Interacción básica con un servicio de red mediante Telnet
- Reconocimiento de configuraciones de autenticación inseguras

## Aprendizaje
Primer contacto con protocolos inseguros y con la importancia de deshabilitar servicios legacy como Telnet en sistemas reales, sustituyéndolos por alternativas cifradas como SSH.

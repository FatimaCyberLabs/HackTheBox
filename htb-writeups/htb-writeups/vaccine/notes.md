# Vaccine — Starting Point (Tier 2)

**Dificultad:** Very Easy · **SO:** Linux · **Categoría:** Cadena completa (acceso + escalada de privilegios)

## Resumen
Primera máquina completa de Tier 2: requiere acceso inicial vía FTP, descifrado de un archivo protegido, acceso SSH, y escalada de privilegios hasta root.

## Herramientas utilizadas
- `nmap`
- `ftp`
- `zip2john` + `john`
- `ssh`
- `sudo -l`

## Metodología

**1. Reconocimiento**
```bash
nmap -sV -p- <IP>
```
Puertos FTP (21) y SSH (22) abiertos.

**2. Acceso inicial (FTP)**
Acceso anónimo revela un archivo `.zip` protegido con contraseña.

**3. Crackeo del archivo**
```bash
zip2john archivo.zip > hash.txt
john hash.txt --wordlist=rockyou.txt
```
Se obtiene la contraseña del zip, que contiene un archivo con credenciales de usuario.

**4. Acceso SSH**
```bash
ssh usuario@<IP>
```
Login con las credenciales obtenidas → **flag de usuario**.

**5. Escalada de privilegios**
```bash
sudo -l
```
Identificación de un binario con permisos `sudo` mal configurado, que permite ejecutar comandos como root sin restricción → **flag de root**.

## Habilidades demostradas
- Cadena de ataque completa: reconocimiento → acceso inicial → movimiento de credenciales → escalada de privilegios
- Crackeo de archivos comprimidos protegidos
- Auditoría de permisos `sudo` para identificar vectores de escalada

## Aprendizaje
Primera cadena de ataque de principio a fin en el portafolio: acceso inicial + reutilización de credenciales + escalada de privilegios. Introduce el concepto de "user flag" y "root flag" en una sola máquina, reflejando un escenario de pentesting real.

# HackTheBox — Starting Point

Portafolio de máquinas completadas en HackTheBox (Starting Point), con notas detalladas sobre metodología, herramientas y conceptos técnicos de cada una.

> ⚠️ Nota: No se publican flags exactas, siguiendo las normas de uso de HackTheBox. El foco está en el proceso, la metodología y las técnicas empleadas.

## Entorno de trabajo
Pwnbox (entorno de ataque en la nube de HTB), usado por limitaciones de hardware local.

## Máquinas completadas

| Máquina | Tier | SO | Categoría principal |
|---|---|---|---|
| [Meow](./meow/notes.md) | 0 | Linux | Servicios inseguros por defecto (Telnet) |
| [Fawn](./fawn/notes.md) | 0 | Linux | Servicios inseguros por defecto (FTP anónimo) |
| [Dancing](./dancing/notes.md) | 0 | Windows | Enumeración SMB |
| [Redeemer](./redeemer/notes.md) | 0 | Linux | Bases de datos expuestas (Redis) |
| [Appointment](./appointment/notes.md) | 1 | Linux | SQL Injection |
| [Sequel](./sequel/notes.md) | 1 | Linux | Bases de datos mal aseguradas (MySQL) |
| [Crocodile](./crocodile/notes.md) | 1 | Linux | Encadenamiento de servicios (FTP → Web) |
| [Responder](./responder/notes.md) | 1 | Windows | Captura y crackeo de hashes NTLM |
| [Three](./three/notes.md) | 1 | Linux | Almacenamiento en la nube mal configurado |
| [Vaccine](./vaccine/notes.md) | 2 | Linux | Cadena completa + escalada de privilegios |
| [Oopsie](./oopsie/notes.md) | 2 | Linux | Control de acceso roto + escalada de privilegios |

## Técnicas y herramientas cubiertas

**Reconocimiento y enumeración**
- Nmap (escaneo de puertos y servicios)
- Enumeración de shares SMB (`smbclient`)
- Enumeración web y de APIs de almacenamiento en la nube

**Explotación**
- SQL Injection para bypass de autenticación
- Control de acceso roto (Broken Access Control) en aplicaciones web
- Captura de hashes NTLM con Responder

**Post-explotación**
- Crackeo de hashes y archivos protegidos (`john`, `hashcat`, `zip2john`)
- Escalada de privilegios en Linux (binarios SUID, capabilities, permisos `sudo` mal configurados)

**Bases de datos**
- Redis sin autenticación
- MySQL con credenciales por defecto

## Progresión

Las máquinas están ordenadas de menor a mayor complejidad dentro de cada tier:
- **Tier 0** — conexión básica a servicios y enumeración inicial
- **Tier 1** — un único paso de explotación por máquina
- **Tier 2** — cadena completa: acceso inicial + escalada de privilegios (flag de usuario y flag de root)

## Siguiente paso

Repaso de teoría (Cisco Cybersecurity Defense Analyst Career Path, preparación autodidacta de CompTIA Security+ vía Professor Messer) de cara a la búsqueda de empleo como analista SOC.

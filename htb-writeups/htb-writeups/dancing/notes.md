# Dancing — Starting Point (Tier 0)

**Dificultad:** Very Easy · **SO:** Windows · **Categoría:** Enumeración SMB

## Resumen
Introducción al protocolo SMB (Server Message Block), ampliamente usado en entornos Windows para compartir archivos e impresoras en red.

## Herramientas utilizadas
- `nmap`
- `smbclient`

## Metodología

**1. Reconocimiento**
```bash
nmap -sV -p 445 <IP>
```
Servicio identificado como `microsoft-ds` (SMB sobre TCP directo).

**2. Enumeración de shares**
```bash
smbclient -L <IP>
```
Listado de todos los recursos compartidos (shares) disponibles en el servidor. Se descartan las shares administrativas por defecto (`ADMIN$`, `C$`, `IPC$`) y se identifica una share de datos accesible.

**3. Acceso**
```bash
smbclient \\\\<IP>\\<share>
```
Conexión a la share identificada con contraseña en blanco.

**4. Descarga**
Dentro del shell SMB (`smb: \>`):
```
get <archivo>
```

**5. Flag**
Localizada en el archivo descargado.

## Habilidades demostradas
- Enumeración de recursos compartidos SMB
- Diferenciación entre shares administrativas y shares de datos
- Descarga de archivos desde un shell SMB interactivo

## Aprendizaje
Primer contacto con enumeración de shares SMB, un vector de ataque muy común en entornos corporativos Windows con configuraciones por defecto o permisos demasiado abiertos.

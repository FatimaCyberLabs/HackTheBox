# Three — Starting Point (Tier 1)

**Dificultad:** Very Easy · **SO:** Linux · **Categoría:** Almacenamiento en la nube mal configurado

## Resumen
Enumeración de un bucket de almacenamiento en la nube (tipo S3) mal configurado y expuesto públicamente sin autenticación.

## Herramientas utilizadas
- `nmap`
- Navegador web / `curl`
- Cliente compatible con S3 (ej. `aws-cli` en modo anónimo)

## Metodología

**1. Reconocimiento**
```bash
nmap -sV -p- <IP>
```
Servicio web identificado, correspondiente a una API de almacenamiento tipo S3.

**2. Enumeración**
Descubrimiento de un bucket accesible sin autenticación al consultar los endpoints estándar del servicio.

**3. Exploración**
```bash
curl <IP>/<bucket>/
```
Listado del contenido del bucket y descarga de los archivos disponibles.

**4. Flag**
Localizada entre los archivos expuestos en el bucket.

## Habilidades demostradas
- Reconocimiento de servicios de almacenamiento en la nube autoalojados
- Enumeración de recursos sin autenticación
- Extracción de datos desde una API de almacenamiento tipo objeto

## Aprendizaje
Muestra un fallo de seguridad muy común en la nube: buckets de almacenamiento con permisos demasiado abiertos, algo que aparece constantemente en informes reales de fugas de datos corporativas.

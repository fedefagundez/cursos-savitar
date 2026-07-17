# Descriptores de archivos

## ¿Qué es un descriptor de archivo?

Un descriptor de archivo es un **número entero** que el kernel asigna a cada archivo abierto por un proceso. Es como un "ticket" o "identificador" que el sistema usa para rastrear qué archivos tiene abiertos un programa.

Los tres descriptores estándar son:

| Descriptor | Nombre | Función |
|:----------:|--------|---------|
| `0` | stdin | Entrada estándar (teclado) |
| `1` | stdout | Salida estándar (pantalla) |
| `2` | stderr | Salida de error (pantalla) |

Los descriptores del `3` al `9` están disponibles para uso personalizado.

---

## `exec` - ¿Para qué sirve?

`exec` reemplaza el proceso actual por otro comando. Pero en el contexto de descriptores, **abre archivos persistentes** que permanecen abiertos durante toda la ejecución del script, sin necesidad de cerrarlos manualmente.

```bash
exec 3<> archivo.txt
```

Esto abre `archivo.txt` para **lectura y escritura** usando el descriptor `3`. El archivo queda abierto mientras el script siga ejecutándose.

---

## `<` y `>` en descriptores

- `<` = **Lectura** (el descriptor lee del archivo)
- `>` = **Escritura** (el descriptor escribe al archivo)

```bash
exec 3< archivo.txt    # Abrir para leer desde el descriptor 3
exec 4> salida.txt     # Abrir para escribir desde el descriptor 4
exec 5<> datos.txt     # Abrir para leer Y escribir desde el descriptor 5
```

---

## `>&` - Redirección entre descriptores

`>&` copia un descriptor a otro. La sintaxis es:

```bash
n>&m
```

Esto significa: "el descriptor `n` ahora apunta a lo mismo que el descriptor `m`".

**Ejemplo:**

```bash
exec 3>&1    # El descriptor 3 ahora apunta a stdout
echo "Hola" >&3    # Escribe "Hola" en stdout (porque 3 = 1)
```

Es útil para **guardar** temporalmente un descriptor y **restaurarlo** después.

---

## Formato append (`>>`)

`>>` agrega contenido al final del archivo **sin sobrescribir** lo que ya existe.

```bash
exec 4>> log.txt    # Abrir log.txt en modo append
echo "Primera línea" >&4
echo "Segunda línea" >&4
# Ambas líneas quedan en el archivo
```

Diferencia:
- `>` = sobrescribe (trunca a 0 bytes)
- `>>` = agrega al final

---

## `n>&-` - Cerrar un descriptor

`>&-` cierra un descriptor de archivo.

**Ejemplo:**

```bash
exec 3> archivo.txt
echo "datos" >&3
exec 3>&-    # Cerrar el descriptor 3
# Ya no se puede escribir en >&3
```

---

## Copias entre descriptores

Puedes copiar descriptores para que dos apunten al mismo archivo:

```bash
exec 3> archivo.txt    # Descriptor 3 escribe al archivo
exec 4>&3              # Descriptor 4 escribe donde 3
exec 3>&-              # Cerrar 3
echo "Esto va por el 4" >&4   # Sigue funcionando por el 4
```

---

## Ejemplo completo: `exec 5<> example` y `exec 6>&5-`

```bash
#!/bin/bash

# Crear archivo de ejemplo
echo "Línea 1" > example.txt

# Abrir example.txt para lectura y escritura con descriptor 5
exec 5<> example.txt

# Leer la primera línea
read linea <&5
echo "Leído: $linea"    # Muestra: Leído: Línea 1

# Escribir algo al final (posición actual del puntero)
echo "Línea 2" >&5

# Copiar descriptor 5 al descriptor 6, y cerrar 5
exec 6>&5-
# Ahora 5 está cerrado, pero 6 sigue apuntando al archivo

# Leer con el descriptor 6
read linea2 <&6
echo "Leído: $linea2"   # Muestra: Línea 2

# Cerrar descriptor 6
exec 6>&-

# Verificar contenido del archivo
cat example.txt
# Resultado:
# Línea 1
# Línea 2
```

### ¿Qué hace `6>&5-`?

Significa: "copiar el descriptor `5` al descriptor `6`, y luego **cerrar** el descriptor `5`". El `-` al final indica que se cierra después de la copia. Es una forma eficiente de **transferir** un descriptor a otro sin mantener ambos abiertos.

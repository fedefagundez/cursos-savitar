# Ejercicios Prácticos - Descriptores de Archivos

## Conceptos básicos

**Ejercicio 1**: ¿Cuáles son los tres descriptores estándar y para qué sirve cada uno?

**Ejercicio 2**: ¿Qué diferencia hay entre el descriptor `0` y el descriptor `3`?

**Ejercicio 3**: ¿Qué hace `exec` en el contexto de descriptores de archivos?

---

## Abrir descriptores con `exec`

**Ejercicio 4**: Abre el archivo `datos.txt` para lectura usando el descriptor `3`

**Ejercicio 5**: Abre el archivo `salida.txt` para escritura usando el descriptor `4`

**Ejercicio 6**: Abre el archivo `registro.txt` para lectura y escritura simultánea usando el descriptor `5`

**Ejercicio 7**: ¿Qué diferencia hay entre `exec 3< archivo.txt` y `exec 3<> archivo.txt`?

---

## Leer y escribir con descriptores

**Ejercicio 8**: Abre `reporte.txt` con el descriptor `3` y lee su contenido línea por línea

**Ejercicio 9**: Escribe "Inicio de registro" en el archivo `log.txt` usando el descriptor `3`

**Ejercicio 10**: Abre un archivo con descriptor `3`, escribe 3 líneas de texto y luego cierra el descriptor

---

## Redirección entre descriptores (`>&`)

**Ejercicio 11**: Copia el descriptor `1` (stdout) al descriptor `5`

**Ejercicio 12**: Redirige el descriptor `3` al descriptor `1` y ejecuta `echo "Hola"`. ¿Qué sucede?

**Ejercicio 13**: ¿Para qué sirve guardar temporalmente stdout en otro descriptor?

---

## Formato append (`>>`)

**Ejercicio 14**: Abre `historial.txt` en modo append usando el descriptor `4`

**Ejercicio 15**: Escribe "Comando 1" y luego "Comando 2" en `historial.txt` usando append. ¿Qué diferencia hay con `>`?

**Ejercicio 16**: ¿Qué pasa si uso `>` en vez de `>>` para agregar contenido a un archivo existente?

---

## Cerrar descriptores (`n>&-`)

**Ejercicio 17**: Abre `archivo.txt` con descriptor `3`, escribe algo y luego cierra el descriptor

**Ejercicio 18**: ¿Qué sucede si intentas escribir en `>&3` después de ejecutar `exec 3>&-`?

**Ejercicio 19**: ¿Por qué es importante cerrar los descriptores?

---

## Copiar descriptores

**Ejercicio 20**: Abre `datos.txt` con descriptor `3`, copia al descriptor `4` y cierra el descriptor `3`

**Ejercicio 21**: Después de ejecutar `exec 4>&3`, ¿qué sucede si escribes en `>&4`?

**Ejercicio 22**: Redirige la salida estándar a un archivo temporalmente usando `exec 4>&1`

---

## Transferir descriptores (`n>&m-`)

**Ejercicio 23**: ¿Qué significa `exec 6>&5-`?

**Ejercicio 24**: Abre `ejemplo.txt` con descriptor `5`, transfíere al descriptor `6` y cierra el `5`

**Ejercicio 25**: Después de `exec 6>&5-`, ¿puedes seguir usando el descriptor `5`?

---

## Ejercicios combinados

**Ejercicio 26**: Abre `entrada.txt` para leer (descriptor `3`) y `salida.txt` para escribir (descriptor `4`), copia el contenido de uno a otro usando los descriptores, y cierra ambos

**Ejercicio 27**: Guarda stdout original en descriptor `5`, redirija stdout a un archivo temporal, ejecuta `ls`, y restaura stdout original desde el descriptor `5`

**Ejercicio 28**: Usa `exec 3<>` para abrir un archivo, lee las primeras 2 líneas, escribe una nueva línea al final, y cierra el descriptor

**Ejercicio 29**: Usa descriptor `3` para escribir en `log1.txt` y descriptor `4` para escribir en `log2.txt`, escribe el mismo mensaje en ambos archivos simultáneamente, y cierra los dos descriptores

**Ejercicio 30**: Usa `exec 5<>` para abrir un archivo existente, luego `exec 6>&5-` para transferir el descriptor, verifica que el descriptor `5` está cerrado y `6` sigue funcionando, cierra el descriptor `6`, y muestra el contenido del archivo final

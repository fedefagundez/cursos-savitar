# Ejercicios Prácticos - Control de Flujo

## Operadores de concatenación

**Ejercicio 1**: Ejecuta `pwd` y `date` en una sola línea usando el operador `;`

**Ejercicio 2**: Escribe un comando que ejecute `ls` solo si `pwd` se ejecuta correctamente.

**Ejercicio 3**: Escribe un comando que muestre un mensaje de error usando `echo "Directorio no encontrado"` solo si `ls carpeta_inexistente` falla.

**Ejercicio 4**: Crea una cadena de tres comandos donde: primero se muestre el directorio actual, luego se liste su contenido, y finalmente se muestre la fecha. Usa `&&` para que cada paso dependa del anterior.

**Ejercicio 5**: Escribe un comando que ejecute `whoami` y solo si tiene éxito, intente listar `/root`. Si falla, muestre "No tengo permisos".

---

## Redirección de salida (stdout)

**Ejercicio 6**: Guarda la salida de `ls -la` en un archivo llamado `listado.txt`

**Ejercicio 7**: Agrega la fecha actual al final del archivo `listado.txt` sin sobrescribir su contenido.

**Ejercicio 8**: Guarda el contenido de `/etc/hostname` en un archivo llamado `info_host.txt`

**Ejercicio 9**: Crea un archivo llamado `numeros.txt` con los números del 1 al 10, uno por línea, usando redirección.

**Ejercicio 10**: Ejecuta `ls` en un directorio inexistente y guarda solo la salida normal en `resultado.txt` (sin errores).

---

## Redirección de errores (stderr)

**Ejercicio 11**: Ejecuta `ls /no_existe` y redirige los errores a un archivo llamado `errores.log`

**Ejercicio 12**: Ejecuta un comando que falle y redirige tanto la salida estándar como los errores al mismo archivo `salida_completa.log`

**Ejercicio 13**: Redirige la salida de `ls /etc` y los errores de `ls /no_existe` a dos archivos diferentes en un solo comando.

**Ejercicio 14**: Ejecuta `cat archivo_inexistente` y redirige los errores al `/dev/null`

**Ejercicio 15**: Crea un script de una línea que ejecute `whoami` y guarde el resultado en `usuario.txt`, pero si falla, guarde el error en `error_usuario.txt`

---

## Uso de /dev/null

**Ejercicio 16**: Ejecuta `ls` y descarta toda la salida (tanto stdout como stderr)

**Ejercicio 17**: Ejecuta un comando que falle y redirige solo los errores al `/dev/null`, mostrando la salida normal en pantalla.

**Ejercicio 18**: Redirige la salida de `ping -c 1 google.com` al `/dev/null` y muestra solo el código de estado.

**Ejercicio 19**: Ejecuta `find / -name "test" 2>/dev/null` y explica por qué se usa la redirección.

---

## Códigos de estado (exit status)

**Ejercicio 20**: Ejecuta `ls` y muestra su código de estado.

**Ejercicio 21**: Ejecuta un comando inexistente y muestra qué código de estado devuelve.

**Ejercicio 22**: Crea un comando que ejecute `ls /etc` y muestre "Éxito" si el código es 0, o "Error" si no lo es.

**Ejercicio 23**: Ejecuta `grep "root" /etc/passwd` y verifica el código de estado. ¿Qué significa?

**Ejercicio 24**: Ejecuta `grep "no_existe" /etc/passwd` y verifica el código de estado. ¿Qué significa?

---

## Ejercicios combinados

**Ejercicio 25**: Crea un comando que intente crear un directorio llamado `test_dir`. Si ya existe, muestre un mensaje indicándolo. Si no existe, lo cree y muestre un mensaje de confirmación.

**Ejercicio 26**: Escribe una línea de comandos que verifique si el archivo `/etc/passwd` existe. Si existe, muéstrame las primeras 3 líneas. Si no, muestra un error.

**Ejercicio 27**: Ejecuta `ls` en tu directorio actual y guarda la salida en `archivo1.txt`, luego ejecuta `ls /etc` y guarda la salida en `archivo2.txt`. Finalmente, concatena ambos archivos en `todos.txt`.

**Ejercicio 28**: Crea un comando que ejecute `date`, guarde la salida en `log.txt`, y luego verifique si el archivo fue creado correctamente.

**Ejercicio 29**: Escribe un comando que intente ejecutar `python3 --version`. Si tiene éxito, muestra "Python instalado". Si falla, muestra "Python no encontrado" y guarda el error en `error_python.log`.

**Ejercicio 30**: Crea un pipeline que liste los archivos del directorio actual, busque los que contengan ".txt", y guarde el resultado en `archivos_txt.txt`. Si no encuentra ninguno, muestra un mensaje apropiado.

---

## Recursos adicionales

| Recurso | Enlace |
|---------|--------|
| Tutorial I/O Redirection (linuxcommand.org) | https://linuxcommand.org/lc3_lts0070.php |
| Advanced Bash-Scripting Guide: I/O Redirection | https://www.tldp.org/LDP/abs/html/io-redirection.html |
| ShellCheck: Errores comunes con && y \|\| | https://www.shellcheck.net/wiki/SC2015 |

# Operadores de control de flujo

`;` - nos permite concatenar comandos en una linea

**Ejemplo**:

```bash
whoami; ls
```

`&&` - concatena los comandos, ejecutando el segundo si y solo sí, el primer comandos devuelve un código de estado exitoso.

**Ejemplo**:

```bash
whoa && ls # En este caso whoa no es un comando válido y no devuelve un código de estado exitos
```

`||` - concatena comandos y en caso de que el primero no devuelva un código de estado no exitoso, ejecuta el segundo.

**`stderr` y `stdout`**

- `stderr` (salida estandar): canal por el que un programa envía su salida normal o los resultados de su ejecución.

- `stdout` (salida de error estándar): canal independiente por el que un programa envía mensajes de error, advertencias o diagnósitcos.

**`/dev/null`**

El `/dev/null` es un tipo de archivo del sistema operativo que funciona como un agujero negro.

- Todo lo que se escriba en ese archivo, es descartado.
- Siempre que se lea ese archivo devolvera **EOF** (end-of-file)

## **Redirectores**

Los _redirectores_ son operadores de shell que permiten cambiar el destino o el origen de los flujos de datos (stdin, stdout, stderr) de un comando.

En lugar de mostrar la salida en la terminal o leer desde el teclado, puedes hacer uqe un comando lea o escriba en archivos, otros comandos o dispositivos especiales `/dev/null`.

| Operador | Función |
|----------|---------|
| `<` | Lee la entrada desde un archivo. |
| `>` | Envía la salida a un archivo (sobrescribe). |
| `>>` | Agrega la salida al final de un archivo. |
| `2>` | Envía los errores a un archivo. |
| `2>&1` | Envía los errores al mismo destino que la salida estándar. |
| `&>` | Envía stdout y stderr al mismo destino (Bash). |

## Ejemplos

```bash
ls > archivos.txt          # Guarda la salida
sort < datos.txt           # Lee desde un archivo
ls error 2> errores.txt    # Guarda solo los errores
comando > salida.log 2>&1  # Guarda salida y errores
comando > /dev/null 2>&1   # Descarta toda la salida
```

## **Redirigir `stderr` y `stdout`**

### Redirigir el `stderr`

El `2` sirve para referenciar el `stderr`.

**Ejemplo**

```bash
whoam 2> /dev/null # Estamos pidiendo que redirija los errores al /dev/null
```
En este caso envía los errores al `/dev/null` pero las salida estandar si se podrá visualizar por consola.

### Redirigir el `stdout`

**Ejemplo**

```bash
cat /etc/hosts > /dev/null # Estamos pidiendo que envíe el stdout al /dev/null
```

### Redirigir el `stderr` al mismo destino de `stdout`

```bash
cat /etc/hosts > /dev/null 2$>1 # Estamos pidiendo que envíe el stdout al /dev/null
```

Alternativa más limpia

```bash
cat /etc/hosts &> /dev/null
```

### Ocultar las salidas de aplicaciones hijas de la consola

**Ejemplo**

```bash
wireshark &> /dev/null 
```

Si queremos que él proceso padre siga funcionando podemos usar el siguiente comando:

```bash
wireshark &> /dev/null & # El último & sirve para dejar el proceso en segundo plano
```

Para independizar el proceso de la consola usamos el siguiente comando

```bash
wireshark &> /dev/null & disown
```

Los `stderr` pueden ser referenciados con `2`.
## **¿Qué son los códigos de estado(`exit status`) en Linux?**

Un código de estado (exit status o exit code) en Linux es un número que devuelve un comando al terminar su ejecución para indicar si se ejecutó correctamente o si ocurrió algún error.

Los códigos de estado indican el resultado de la ejecución de un comando.

| Código | Significado |
|:------:|-------------|
| `0` | Éxito. El comando se ejecutó correctamente. |
| `1` | Error general. |
| `2` | Uso incorrecto del comando o error de sintaxis. |
| `126` | El archivo existe, pero no tiene permisos de ejecución. |
| `127` | Comando no encontrado. |
| `128` | Argumento inválido para `exit`. |
| `128 + n` | El proceso terminó por una señal (`n` es el número de la señal). |
| `130` | Proceso interrumpido con `Ctrl + C` (`SIGINT`, señal 2). |
| `137` | Proceso terminado con `SIGKILL` (señal 9), por ejemplo por `kill -9` o por falta de memoria (OOM Killer). |
| `139` | Error de segmentación (`Segmentation Fault`, `SIGSEGV`, señal 11). |
| `143` | Proceso terminado con `SIGTERM` (señal 15). |
| `255` | Error de salida fuera del rango válido o fallo grave del programa. |

### Consultar el código de estado del último comando

```bash
echo $?
```

### Ejemplos

```bash
ls
echo $?     # 0
```

```bash
ls carpeta_inexistente
echo $?     # 2
```

```bash
comando_que_no_existe
echo $?     # 127
```

### Nota

- `0` = éxito.
- Cualquier valor distinto de `0` indica un error o una condición especial.
- Los programas pueden definir sus propios códigos entre `1` y `125`, aunque existen convenciones ampliamente utilizadas.
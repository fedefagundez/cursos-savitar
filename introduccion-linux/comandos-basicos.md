# Comandos básicos Linux

`whoami` - saber cuál es el usuario actual.

`id` - conocer los grupos del usuario actual.

`sudo` - ejecutar un comando con privilegios de otro usuario (normalmente `root`).

`sudo su` - cambiar al usuario `root` (administrador del sistema).

Los grupos se pueden ver en la siguiente ruta: `/etc/group`.

`cat` - muestra el contenido de un archivo. Por ejemplo:

```bash
cat /etc/group
```

`cat -n` - muestra el contenido del archivo indicando los números de línea.

Ver contenido en formato paginado: `less`.

**Los comandos de control son:**

- `Espacio` - página siguiente.
- `b` - página anterior.
- `Enter` - baja una línea.
- `/texto` - busca una palabra.
- `n` - siguiente coincidencia.
- `q` - salir.

`which` - muestra la ruta absoluta de un comando. Por ejemplo:

```bash
which cat
```

**Alternativas a `which`:** `commnad -v whoami`

`echo` - imprime texto en pantalla.

`echo $PATH` - imprime el contenido de la variable de entorno `PATH`.

`echo $HOME` - imprime la ruta del directorio personal del usuario.

`|` (pipe) - redirige la salida de un comando hacia otro.

`grep "texto"` - filtra las líneas que contienen el texto indicado.

**Ejemplo:**

```bash
cat /etc/group | grep "floppy"
```

**Con números de línea:**

```bash
cat /etc/group | grep -n "floppy"
```

`ls` - listar todos las carpetas y archivos del directorio
`ls -l` - listar todos las carpetas y archivos del directorio con detalles  
`pwd` - mostrar el directorio actual  
`cd ..` -  cambiar al directorio padre  
`cd directorio` - cambia al directorio indicado
`cd` - cambia al directorio home del usuario

`/etc/passwd` guarda los datos de todos lo usuarios, id del usuario, id del grupo, dirección del directorio HOME, la shell utilizada

En `/etc/shells` están los shells disponibles

## Formato del archivo `/etc/passwd`

El archivo **`/etc/passwd`** almacena la información básica de las cuentas de usuario del sistema. Cada usuario ocupa **una línea** y los campos están **separados por dos puntos (`:`)**.

## Formato

```text
nombre_usuario:contraseña:UID:GID:GECOS:directorio_home:shell
```

## Descripción de los campos

| Campo | Descripción |
|--------|-------------|
| **nombre_usuario** | Nombre de la cuenta del usuario. |
| **contraseña** | Normalmente contiene `x`, indicando que la contraseña cifrada se almacena en `/etc/shadow`. |
| **UID** | Identificador numérico único del usuario (*User ID*). |
| **GID** | Identificador numérico del grupo principal del usuario (*Group ID*). |
| **GECOS** | Información adicional del usuario, como nombre completo, oficina o teléfono. Puede estar vacío. |
| **directorio_home** | Ruta al directorio personal del usuario. |
| **shell** | Intérprete de comandos que se ejecuta al iniciar sesión (por ejemplo, `/bin/bash` o `/bin/sh`). |

## Ejemplo

```text
federico:x:1000:1000:Federico Pérez:/home/federico:/bin/bash
```

### Significado

- **Usuario:** `federico`
- **Contraseña:** `x` (la contraseña está almacenada en `/etc/shadow`)
- **UID:** `1000`
- **GID:** `1000`
- **GECOS:** `Federico Pérez`
- **Directorio personal:** `/home/federico`
- **Shell:** `/bin/bash`
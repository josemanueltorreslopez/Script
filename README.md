# Script
## Ejercicios de Script
### Ejer 1: Eliminacion de Directorio o archivo.

```` 
# Elimina un archivo o directorio pasado como parámetro, y le pregunte si está seguro de llevar a cabo la acción.
#! /bin/bash

clear
if [ -e $1 ]
then
	if [ -d $1 ]
	then
		read -p "¿Esta seguro?(Y/N) " opcion
		if [ $opcion == "Y" -o $opcion == "y" ]
		then
			rm -r $1
			exit 0
		fi
		exit 1
	else
		read -p "¿Esta seguro?(Y/N) " opcion
		if [ $opcion == "Y" -o $opcion == "y" ]
		then
			rm $1
			exit 0
		fi
		exit 1
	fi
else
	echo "No existe el fichero o el directorio dado como parametro."
fi
````

### Ejer 2: Muestra la ayuda de un comando pasado como parametro.

````
# Muestra la información de un comando al ejecutar dicho script y pasar como parámetro el comando.
#! /bin/bash

clear
$1 --help
````

### Ejer 3: Comprobacion de usuario "blas" y si es asi lo muestra 5 veces.

````
# Comprueba si el usuario actual del sistema es blas, si es así visualiza su nombre 5 veces, sino te despides de él amigablemente.
#! /bin/bash

clear
usuario=`whoami`
if [ $usuario == 'blas' ]
then
	echo $usuario
	echo $usuario
	echo $usuario
	echo $usuario
	echo $usuario
else
	echo "Hasta luego."
fi
````
### Ejer 4: Muestra si la palabra clave de un archivo.

````
# Muestra si la palabra clave de un archivo es el parámetro pasado o no.
#/!bin/bash

clear
clave=`cat /home/usuario/Documents/fichero.sh`
if [ $clave == $1 ]
then
	echo "Si"
else
	echo "No"
fi
````


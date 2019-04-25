# Script
## Ejercicios de Script
### Ejer 1 Eliminacion de Directorio o archivo.
```` #! /bin/bash

# Elimina un archivo o directorio pasado como parámetro, y le pregunte si está seguro de llevar a cabo la acción.

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

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
### Ejer 5: Menu con suma,resta o multiplicacion.

````
# Suma, resta o multiplica según le indiquemos en el menú.
#! /bin/bash

clear
while [ true ]
do
	read -p "Introduce 1:Sumar, 2:Restar, 3:Multiplicar y 4:Salir" opcion
	case $opcion in
		1)
			read -p "Primer número " n1
			read -p "Segundo número " n2
			su=`expr $n1 + $n2`
			echo $n1" + " $n2 " = "$su
		;;
		2)
			read -p "Primer número " n1
			read -p "Segundo número " n2
			re=`expr $n1 - $n2`
			echo $n1" - " $n2 " = "$re
		;;
		3)
			read -p "Primer número " n1
			read -p "Segundo número " n2
			mu=`expr $n1 \* $n2`
			echo $n1" * " $n2 " = "$mu
		;;
		*)
			exit 0
		;;
	esac
done
````

### Ejer 6: Pide la edad y dice si es mayor o menor de edad.

````
# Pide la edad y nos dice si es mayor de edad o menor.
#! /bin/bash

clear
read -p "Introduce tu edad: " edad
if [ $edad -lt 18 ]
then
	echo "Eres menor de edad "
else
	echo "Eres mayor de edad"
fi
````

### Ejer 7: Verificaciond e si un fichero existe, si es de lectura-escritura y le añade ejecutable para grupo y usuarios.

````
# Recibe un nombre de fichero, verifica que existe y que es un fichero de lectura-escritura, lo convierte en ejecutable para el usuario y el grupo y muestra el estado final de los permisos.
#/!bin/bash

clear
if [ -f $1 ]
then
    	if [ -r $1 ]
	then
		if [ -w $1 ]
		then
			chmod ug+x $1
			ls -l $1
		else
			echo "El fichero no tiene permisos de lectura-escritura"
        fi

    else
    echo "El fichero no tiene ni permisos de escritura ni de lectura"

    fi

else
echo "El fichero no existe"
fi
````
### Ejer 8: Pulsamos una tecla y nos dice si es letra, numero o caracter
````
# Nos dice al pulsar una tecla si es una letra, numero o caracter especial.
#/!bin/bash

read -p "Introduce el carácter " caracter
case $caracter in
	[a-z,A-Z])
		echo "Se ha introducido una letra"
	;;
	[0-9])
		echo "Se ha introducido un número"
	;;
	*)
		echo "Se ha introducido un caracter especial"
	;;
esac

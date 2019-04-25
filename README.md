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

### Ejer 8: Pulsamos una tecla y nos dice si es letra, numero o caracter.

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
````

### Ejer 9: Dice de todos los parametros pasados cuantos son directorios y cuantos archivos.

````
# Recibe varios parametros y nos dice cuantos de esos parametros son de directorios y cuantos son archivos.
#/!bin/bash

clear
contador=0
contadorFicheros=0
for indice in $@
do
	if [ -d $indice ]
	then
		contador=`expr $contador + 1`
	elif [ -f $indice ]
	then
		contadorFicheros=`expr $contadorFicheros + 1`
	fi
done
echo "El total de directorios es: $contador"
echo "El total de archivos es: $contadorFicheros"
````

### Ejer 10: Maquina de refrescos.

````
# Mostramos menu, con productos para vender, luego nos pide que introduzcamos la opcion. luego mensaje que indica que introduzca moneda.
# Si ponemos precio exacto nos da mensaje, "Gracias buen provecho", si ponemos menos, nos diga falta. 
# Si poner mas valor, nos indique el cambio con mensaje.
#/!bin/bash

clear
read -p "Introduce una opción: 1) Cocacola 2)Fanta 3)Salir: " opcion
case $opcion in
	1)
		read -p "Introduce 1 euro: " dinero
		if [ $dinero -lt 1 ]
		then
			echo "Falta dinero"
		elif [ $dinero -eq 1 ]
		then
			echo "Gracias buen probecho"
		elif [ $dinero -gt 1 ]
		then
			echo "El cambio"
		fi
	;;
	2)
		read -p "Introduce 3 euro: " dinero
		if [ $dinero -lt 3 ]
		then
			echo "Falta"
		elif [ $dinero -eq 3 ]
		then
			echo "Gracias buen probecho"
		elif [ $dinero -gt 3 ]
		then
			echo "El cambio"
		fi
	;;
	*)
		exit 0
	;;
esac
````

### Ejer 11: Nos da la ruta de un directorio y contamos los archivos y directorios que hay.

````
# Nos pide introducir la ruta de un directorio por teclado y nos dice cuantos archivos y cuantos directorios hay dentro de 
# ese directorio.
#/!bin/bash

clear
read -p "Introduzca la ruta de un directorio :" directorio
until [ -d $directorio ]
do
	read -p "Introduzca la ruta de un directorio :" directorio
done
directorios=0
ficheros=0
for indice in `ls $directorio`
do
	if [ -d $indice ]
	then
		contador=`expr $directorios + 1`
	elif [ -f $indice ]
	then
		ficheros=`expr $contadorFicheros + 1`
	fi
done
echo "Ha introducido un total de $directorios directorios y un total de $cficheros ficheros."
````

### Ejer 12:  Tabla de multiplicar.

````
# Introduce un número por parámetro y muestra su tabla de multiplicar
#/!bin/bash

clear
echo "--- La tabla de multiplicar del $1 ---"
for (( indice=0; indice<11; indice++ ))
do
   resultado=`expr $1 \* $indice`
   echo "$1 x $indice = $resultado"
done
````
### Ejer 13: Limpieza de reglas y permisos de las conexiones.

````
# Limpia todas las reglas, y da permiso a todas las conexiones.
#/!bin/bash

clear
iptables -F
iptables -A INPUT -j ACCEPT
iptables -A OUTPUT -j ACCEPT
iptables -A FORWARD -j ACCEPT
````

### Ejer 14: Limpieza de reglas y prohibicion de todas las conexiones.

````
# Limpia todas las reglas, y prohíbe cualquier conexión.
#/!bin/bash

clear
iptables -F
iptables -A INPUT -j DROP
iptables -A OUTPUT -j DROP
iptables -A FORWARD -j DROP
````

### Ejer 15: Permios de iptables a una ip.

````
# Se introducen tres parámetros: red(ip), entrada-salida, aceptar-denegar. Dá estos permisos a iptables.
#/!bin/bash

clear
if [ $2 == "entrada" ]
then
	if [ $3 == "aceptar" ]
	then
		iptables -A INPUT -s $1 -j ACCEPT
	fi
fi
if [ $2 == "entrada" ]
then
	if [ $3 == "denegar" ]
	then
		iptables -A INPUT -s $1 -j DROP
	fi
fi
if [ $2 == "salida" ]
then
	if [ $3 == "aceptar" ]
	then
		iptables -A INPUT -d $1 -j ACCEPT
	fi
fi
if [ $2 == "salida" ]
then
	if [ $3 == "denegar" ]
	then
		iptables -A INPUT -d $1 -j DROP
	fi
fi

# Laboratorio Sobrevieviendo a VIM

## ¿Eres nuevo en VIM? Relajate, Con este laboratorio vas a subir más de un nivel. 
No te preocupes con este pequeño manual podrás realizar todas las acciones que realizas en cualquier editor de texto, pero con una gran ventaja, no vas a necesitar el ratón para nada :wink:

Ahora si abre tu terminal y preparate para disfrutar del siguiente laboratorio.
He creado el laboratorio para ir viendo paso a paso las diferentes secciones que veremos en el curso.

Si en cualquier momento te lias y no sabes conocer en evolver al punto anterior, no entres en **pánico** siempre puedes volver atrás pulsando la tecla ```ESC``` varias veces y pulsando luego la tecla ```u``` que significa **undo** en español deshacer, jejeje o si lo prefieres puedes cerrar el fichero sin guardar los cambios pulsando ```:q!```

## Escenario planteado

Eres un administrador de sistemas y te encuentras que en tu nueva empresa todos los sistemas linux solo tienen instalado el editor VIM por lo que vas a necesitar aprender a usarlo si o si, no hay otra solución si no quieres el despido inmediato.

No te queda otra que sentarte delante de este laboratorio para obtener las habilidades necesarias usando el editor Vim y evitar que te despidan por algo tan sencillo :wink:

Te aseguro que una vez finalices este laboratorio tendrás los conocimientos necesarios para evitar ese despido. Asi que vamos al turrón...

# Crear, Abrir y Salir de un fichero

## Crear y guardar un fichero con Vim

1. Abrir Vim:

```bash
vim
```

2. Ahora nos toca insertar texto en el fichero asi que pulsa la tecla ```i``` verás que en la parte abajo a la izquierda has cambiado al **Modo Insertar**. Escribe ahora el texto que quieras tener en este fichero.

3. Una vez que tengas todo el texto escrito pulsa la tecla ```ESC``` para volver al **Modo Comando**
4. Ahora nos toca guardarlo y salir de vim para guardar el fichero en disco con el nombre 'mifichero.txt' escribiremos lo siguiente:
```bash
:w mifichero.txt

#La 'w' significa write
```

5. Ahora queremos cerrar vim para ello pulsamos:
```bash
:q

# La 'q' significa quit
```

**NOTA:** Puedes guardar y salir lanzando el siguiente comando, evitando tener que hacer el paso 4 y 5 y haciendolo en un solo paso:
```bash
:wq
```

## Editar un fichero y salir sin guardar cambios

1. Editar el fichero ```/etc/hosts ```
```bash
vim /etc/hosts
```
2. Al pulsar la tecla ```i``` entramos en el modo insercción pero nos va a dar un error ya que el fichero es de solo lectura ya que solo root puede editarlo
```bash
W10: Warning: Changing a readonly file
```
3. Intentaremos salid salir del fichero pulsando la tecla ```ESC``` y despues la combinación de teclas ```:q```  **Este paso no funciona y no podemos salir**

4. Para forzar la salida debemos pulsar ```ESC``` y después ```:q!```


## Realizar cambios a un fichero

1. Vamos a copiar la documentación de Vim a nuestra carpeta para tener un fichero con texto

```bash
cp /usr/share/vim/vim80/doc/help.txt ~/vimhelp.txt
```
**NOTA:** El directorio vim80 puede no existir lo recomendable es que escribas 
```bash 
cp /usr/share/vim/vim #Aqui dale a la tecla TAB para que te lo autocomplete
``` 
Luego rellena el resto de la ruta /doc/help.txt


2. Editamos el fichero escribiendo:

```bash
vim ~/vimhelp.txt
``` 
3. Nos movemos hasta el texto **VIM - main help file**

**NOTA:** Para movernos por el fichero tenemos dos formas de hacerlo, más abajo tenmos mas formas de movernos por nuestro fichero agilmente.
- Con los cursores / flechas del teclado
- En caso de que nuestro teclado no disponga de las teclas cursores n os podemos mover con las teclas 

```h```  ```j```  ```k```  ```l```
	
```bash
	h -->  nos movemos a la izquierda
	j -->  nos movemos hacia abajo
	k -->  nos movemos hacia arriba
	l -->  nos movemos hacia la izquierda
	#RECUERDA:para movernos por el texto debemos estar en el modo comando por lo que debes pulsar la tecla ESC 
```



4. Cambiamos la palabra VIM a Vim para ello colacomas el curso en la letra i y pulsamos ```cw``` para cambiar el resto de la palabra **im**
**NOTA:** La tecla ```c``` en modo comando nos sirve para hacer cambios por lo que nos quita la letra, palabra o linea depende de como lo mandemos y se pasa a modo inserción para poder escribir directamente.

5. Ahora pulsa ta tecla ```ESC``` para salir del modo comando
6. Ahora muevete hasta la letra i y pulsa 2 veces la tecla ~ 
**NOTA:** La tecla ~ en modo comando nos cambia la letra donde este el curso de Mayúscula a Minúscula y de Minúscula a Mayúscula 
7. Ahora navega hasta la letra h de la palabra help y pulsa 3 veces la tecla ~ covirtiendo de este modo la palabra help a mayúsculas
8. Pulsa la tecla ```ESC``` para asegurarte que vuelves al modo comando
9. Guardamos y salimos pulsando:
```bash
:wq
```

## Movernos por nuestro fichero agilmente

1. Editamos nuestra copia del fichero **vimhelp.txt**
```bash
vim ~/vimhelp.txt 
```
2. Para ir al final del fichero pulsamos ```G```
3. Subir al principio del fichero pulsamos ```gg```
4. Para movernos a la linea 15 podemos hacerlo pulsando  ```15G``` o ```:15```
 

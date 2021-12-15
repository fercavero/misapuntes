# Laboratorio Sobrevieviendo a VIM

## ¿Eres nuevo en VIM? Relajate, Con este laboratorio yo te voy a ayudar. 
No te preocupes con este pequeño manual podrás realizar todas las acciones que realizas en cualquier editor de texto, pero con una gran ventaja, no vas a necesitar el ratón para nada ;)

Ahora si abre tu terminal y preparate para disfrutar del siguiente laboratorio.
He creado el laboratorio para ir viendo paso a paso las diferentes secciones que veremos en el curso.

Si en cualquier momento te lias y no sabes conocer en evolver al punto anterior, no entres en **pánico** siempre puedes volver atrás pulsando la tecla ```ESC``` varias veces y pulsando luego la tecla ```u``` que significa **undo** en español deshacer, jejeje o si lo prefieres puedes cerrar el fichero sin guardar los cambios pulsando ```:q!```

## Escenario planteado

Eres un administrador de sistemas y te encuentras que en tu nueva empresa todos los sistemas linux solo tienen instalado el editor VIM por lo que vas a necesitar aprender a usarlo si o si, no hay otra solución si no quieres el despido inmediato.

No te queda otra que sentarte delante de este laboratorio para obtener las habilidades necesarias usando el editor Vim y evitar que te despidan por algo tan sencillo ;)

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
2. Al pulsar la tecla ```i``` entramos en el modo Isercción pero nos va a dar un error ya que el fichero es de solo lectura ya que solo root puede editarlo
```bash
W10: Warning: Changing a readonly file
```
3. Intentaremos salid salir del fichero pulsando la tecla ```ESC``` y despues la combinación de teclas ```:q```  **Este paso no funciona y no podemos salir**

4. Para forzar la salida debemos pulsar ```ESC``` y después ```:q!```



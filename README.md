# Documentación SafeEmail

## Integrantes:
- Esteban Trujillo Carmona
- Juan Esteban Avendaño
- Viviana Hoyos Sierra
- julian Romero Hinestroza
- Damián Duque López

## SetUp:
Para poder utilizar SafeEmail correctamente será necesario que el usuario genere una contraseña especial para su cuenta de Google, la cual será utilizada por SafeEmail al momento de acceder a su correo electrónico.
Este proceso es completamente seguro y se explicara a continuación:

1. Ir a sección de "Gestionar mi cuenta" de Google
2. Hacer clic en “Seguridad”
3. Se debe de activar la "Verificación en dos pasos" en caso de que no se haya hecho antes.
4. Entrar a la siguiente dirección: https://myaccount.google.com/u/4/apppasswords
Para crear la nueva contraseña que utilizara dentro de SafeEmail el usuario debe de ingresar un nombre y hacer clic en el botón que dice "Crear", una vez haga esto una nueva ventana aparece indicando cuál es su nueva contraseña. Por favor guárdela con cuidado, ya que esta será la única vez en la podrá verla y será necesaria para el funcionamiento del programa más adelante.
La ventana emergente con la nueva contraseña debe verse similar a esta:

![SetUp](https://github.com/EsteTruji/SafeEmail/assets/94024545/11c832fc-1aca-4b5d-b3af-dff0c2199be4)


## Uso de SafeEmail:
Los 2 principales servicios que ofrece SafeEmail son: El envió de archivos y documentos encriptados por medio de correo electrónico y la desencriptación de archivos. Para utilizarlos el usuario deberá de ejecutar el archivo "main.py" con los parámetros correspondientes, los cuales serán explicados a continuación:

## Envió de documentos:

Para realizar un envió de algún archivo encriptado el usuario deberá ejecutar el código respetando el siguiente formato:
```python
python main.py send <received_file> <key> <my_mail> <second_key> <auth_key>
# Comando de ejemplo:
python main.py send test.txt damianduquel@gmail.com damianduquel2@gmail.com nrvs rzju rmnh mozw
```

Una vez ejecutado el comando y si las validaciones son correctas, SafeEmail se encargará de realizar las siguientes tareas:
1. Encriptar el documento elegido por el usuario
2. Enviar un correo electrónico al destinatario con el nuevo documento encriptado como archivo adjunto
3. Enviar un tercer correo al destinatario con la clave necesaria para desencriptar el archivo

Demostración de funcionamiento:

Archivo original:
![image](https://github.com/EsteTruji/SafeEmail/assets/94024545/7d8713a1-8b65-4c5a-b944-a9131a680108)

Output del programa:
![image](https://github.com/EsteTruji/SafeEmail/assets/94024545/228d6c98-bd40-4e4e-83e0-15a6b4dd82ff)

Archivo encriptado:
![image](https://github.com/EsteTruji/SafeEmail/assets/94024545/2b49b037-440d-4647-b226-61c44b9bbbad)

Correos electrónicos enviados por SafeEmail:
![image](https://github.com/EsteTruji/SafeEmail/assets/94024545/48a1eabd-7aaa-40f7-afd5-788fd19af0f1)

## Desencriptación de archivos:

Para desencriptar un archivo el usuario deberá ejecutar el código respetando el siguiente formato:
```python
python main.py decrypt <received_file> <key> <my_mail> <second_key> <auth_key>
# Comando de ejemplo:
python main.py decrypt test-enc.txt e740ea3d93a8b71bd97d48477b33ca53 damianduquel@gmail.com damianduquel2 nrvs rzju rmnh mozw
```
Una vez ejecutado el comando y si las validaciones son correctas, SafeEmail se encargará de realizar las siguientes tareas:
1. Desencriptar el documento elegido por el usuario
2. Enviar un correo electrónico al remitente original del archivo informándole que el documento que envió fue desencriptado correctamente.

Demostración de funcionamiento:

Output del programa:
![image](https://github.com/EsteTruji/SafeEmail/assets/94024545/55cc2182-52fe-45c6-bbe1-1b69153f6412)

Archivo desencriptado:
![image](https://github.com/EsteTruji/SafeEmail/assets/94024545/b7e8becc-9fab-41bf-8c6e-86647a316977)

Correo electrónico enviado por SafeEmail:
![image](https://github.com/EsteTruji/SafeEmail/assets/94024545/38419615-39e0-42d9-af65-7e9eb2f06ada)

# Funcionamiento del código:
El funcionamiento de SafeEmail depende principalmente de los parámetros que envíe el usuario al momento de ejecutar el código, siendo estos los que definirán las acciones que realizara el sistema y los valores que utilizaran para realizar dichas tareas. A continuación, podremos evidenciar el apartado del código en el que se verifica la acción elegida por el usuario (Especificada en el primer parámetro) para luego guardar los demás parámetros en variables, verificar la validez de los valores y en caso de que no se encuentre ningún error, iniciar los procesos necesarios para cumplir con los deseos del usuario.)

![image](https://github.com/EsteTruji/SafeEmail/assets/94024545/5a5520e4-a4ef-43ef-83eb-e133af50a033)
![image](https://github.com/EsteTruji/SafeEmail/assets/94024545/524119c1-e55c-42d4-b9e7-06d69f6c37a5)

## Envió de documentos:
Una vez se han guardado los parámetros enviados por el usuario y se haya verificado la existencia del archivo, el código procederá a generar las claves de encriptación, la primera de forma aleatoria y asignándole un valor a la clave secundaria en base al usuario del correo electrónico de la persona a la que se le enviara el archivo. Posteriormente se inicia el proceso de encriptación.

![image](https://github.com/EsteTruji/SafeEmail/assets/94024545/fffdfa53-b8f0-4b15-9818-116813633d86)

Para realizar la encriptación del archivo el sistema simplemente lee el contenido del archivo original y lo encripta utilizando el módulo AES, pasando como parámetro la clave generada aleatoriamente en el paso anterior

![image](https://github.com/EsteTruji/SafeEmail/assets/94024545/0e240382-fab4-4be2-aaf0-0dd12f4e4e0a)

Posteriormente, a la hora de crear el nuevo archivo encriptado con mayor seguridad se procede a escribir en un nuevo documento el contenido cifrado del archivo original, en conjunto con la clave secundaria y la dirección de correo electrónico del remitente. Estos dos últimos valores se incluyen dentro del documento con el propósito de incrementar la dificultad de descripción para un tercero y también para garantizar que el sistema pueda identificar fácilmente al usuario que envió el archivo para poder notificarle cuando este sea descomprimido.

![image](https://github.com/EsteTruji/SafeEmail/assets/94024545/9016be70-5645-4ea3-9505-d31a818905ec)

Por último, una vez se ha completado el proceso de encriptado el sistema procederá a enviar 2 correos electrónicos al destinatario indicado por el usuario. En el primer correo se incluirá el documento comprimido como archivo adjunto y en el segundo se enviará la clave que será necesaria para descomprimir el archivo. Este proceso se puede evidenciar en el siguiente código:

![image](https://github.com/EsteTruji/SafeEmail/assets/94024545/558b60e2-cd3d-4b26-881c-27cb4a8e44fe)
![image](https://github.com/EsteTruji/SafeEmail/assets/94024545/21a0b4e1-8c06-4888-81f8-bb17ba6d58b2)
![image](https://github.com/EsteTruji/SafeEmail/assets/94024545/5063c049-5186-4f0d-8785-dc6ea3bb3aa9)


## Desencriptación de archivos:
Una vez se han guardado los parámetros enviados por el usuario y se haya verificado la existencia del archivo, el código procederá iniciar el proceso de desencriptado

![image](https://github.com/EsteTruji/SafeEmail/assets/94024545/6d8e616c-6ac0-45db-913c-f1bc9dfc7ff4)

Al iniciar el proceso de desencriptado, el primer paso será extraer la dirección de correo electrónico del remitente original del archivo para poder enviarle un correo de confirmación en caso de que el documento sea desencriptado exitosamente, luego, Se procederá a verificar que el valor de la segunda clave ingresada por el usuario coincida con la segunda clave presente en el archivo, en caso de que estas sean diferentes se le notificara al usuario que la segunda clave que ingreso es incorrecta.

![image](https://github.com/EsteTruji/SafeEmail/assets/94024545/5d6927a4-734d-4b72-a271-29cc92f5b21e)

En caso de que se compruebe exitosamente que el valor de la segunda clave ingresada por el usuario es correcta, el programa se encargara de desencriptar el archivo

![image](https://github.com/EsteTruji/SafeEmail/assets/94024545/85973ae5-bf91-4aba-b000-605cf1b53777)

Posteriormente, se creara un diccionario que cumplirá la labor de logear la acción realizada por el sistema.

![image](https://github.com/EsteTruji/SafeEmail/assets/94024545/3092201e-7fd0-49d3-92dd-a38991d8a37a)

Por último, una vez se ha desencriptado el archivo y se ha logeado la acción de manera exitosa se procederá a enviar un correo electrónico al remitente original del archivo en el que se le informara que este fue desencriptado exitosamente utilizando la información recogida en el log creado en el paso anterior

![image](https://github.com/EsteTruji/SafeEmail/assets/94024545/3e1bdb4c-e3bb-4a7c-93b5-243c4802ae74)

![image](https://github.com/EsteTruji/SafeEmail/assets/94024545/d0976ff1-285b-443b-a8d2-ab6fdbf1c94c)

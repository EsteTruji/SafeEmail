# Documentación SafeEmail

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
python main.py decrypt <received_file> <key> <my_mail> <second_key> <auth_key>
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

Archivo comprimido:
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

Archivo descomprimido:
![image](https://github.com/EsteTruji/SafeEmail/assets/94024545/b7e8becc-9fab-41bf-8c6e-86647a316977)

Correos electrónico enviado por SafeEmail:
![image](https://github.com/EsteTruji/SafeEmail/assets/94024545/38419615-39e0-42d9-af65-7e9eb2f06ada)


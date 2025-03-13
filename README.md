# Jenkins Lab

## Ejecutar Docker Compose

Para ejecutar Docker Compose, asegúrate de que tengas Docker Compose instalado en tu sistema. Luego, sigue estos pasos:

1. Navega a la ubicación donde se encuentra tu archivo `docker-compose.yml`.

2. Ejecuta el siguiente comando en tu terminal para iniciar los contenedores definidos en el archivo `docker-compose.yml`:

```bash
docker-compose up -d
```

3. Extraer passwords

```bash
docker logs id_container
```

```bash
docker exec id_container cat /var/jenkins_home/secrets/initialAdminPassword
```
### Kevin Steven Nieto Curaca - A00395466

Se comprueba entonces la ejecución del contenedor habiendo ingresado la contraseña dada por el comando cat dentro del contenedor.

![image](https://github.com/user-attachments/assets/2c6831c2-7ed9-46c4-b8a0-ba7204bd645a)

Se instala el plugin de nodejs, para poder usar los comandos de node dentro de Jenkins.

![image](https://github.com/user-attachments/assets/5548a334-5892-4f5c-8326-b1100efb3f4f)

Nos vamo entonces a la sección de Tools para habilitar las dependencias o plugins necesarios. Se debe especificar la versión del node, en particular la aplicación se ejecuta en la 10.15.2

Luego, de activar node en los tools se procede a crear un job para el pipeline.


Para ello se debe especificar la opción de aplicar los cambios a un repo, indicando la rama donde se va a ejecutar el job.

En envirotments se debe habilitar la elcción del providenode 

Build steps -> Se debe ejecutar desde shell.


Se agregan los comandos para desplegar: 
1. npm i
2. npm run build
3. npm run start
4. node app.js

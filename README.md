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
Antes de toda la instalación se debe crear un volumen para que, en caso tal de que se apague Jenkins, las configuraciones persistan.
Además de ello, se agrega un port forwarding del puerto 3000 para que se pueda acceder a la app que se va a ejecutar dentro de jenkins.

![image](https://github.com/user-attachments/assets/110f7cc3-104c-4333-b6e6-234f23b8a5b5)

Se comprueba entonces la ejecución del contenedor habiendo ingresado la contraseña dada por el comando cat dentro del contenedor.

![image](https://github.com/user-attachments/assets/2c6831c2-7ed9-46c4-b8a0-ba7204bd645a)

Se instala el plugin de nodejs, para poder usar los comandos de node dentro de Jenkins.

![image](https://github.com/user-attachments/assets/5548a334-5892-4f5c-8326-b1100efb3f4f)

Nos vamos entonces a la sección de Tools para habilitar las dependencias o plugins necesarios. Se debe especificar la versión del node, en particular la aplicación se ejecuta en la 10.15.2

![image](https://github.com/user-attachments/assets/f4c6b5ed-2457-4530-9b81-dcc5ca4d148e)

Luego de activar node en los tools, se procede a crear un job para el pipeline de tal manerar que se vincule con el repositorio y la rama en particular.

Para ello se debe especificar la opción de aplicar los cambios a un repo e indicar la rama donde se va a ejecutar el job.

![image](https://github.com/user-attachments/assets/8e850151-9ae4-477e-894c-9ec7f79dd770)


En enviroments se debe habilitar la elección del providenode para poder realizar la ejecución de los comandos de node.

Enviroment:
![image](https://github.com/user-attachments/assets/0c9f5888-2305-4ea6-a022-996a94f80af1)

Se habilita la shell:
![image](https://github.com/user-attachments/assets/ac66a6f2-4747-4056-8d7a-a105694c3ff5)


Para la ejecución de la app es necesario establecer una shell que nos permita indicar los comandos a ejecutar.
Se agregan los comandos para desplegar: 
1. npm i
2. npm run build
3. npm run start &
Nota: cabe recalcar que se usa el `&` para liberar el job de jenkins.

Se verifica entonces la ejecución servidor:

![image](https://github.com/user-attachments/assets/26279765-fe7d-484e-b4f2-15c2614f9387)


Por último se comprueba que se pueda obtener el mensaje del server en el puerto 3000.

![image](https://github.com/user-attachments/assets/832d4470-7dd0-484e-bd23-0f0001c348de)

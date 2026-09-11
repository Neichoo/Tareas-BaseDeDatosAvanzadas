# Tarea 1: MongoDB

Configuración de un replica set de MongoDB mediante Docker y ejecución de las consultas del informe.

## Requisitos

- [MongoDB Community Server](https://www.mongodb.com/try/download/community) instalado.
- [MongoDB Compass](https://www.mongodb.com/try/download/compass) instalado.
- [Docker Desktop](https://www.docker.com/products/docker-desktop/) instalado y en ejecución.

## Iniciar MongoDB

1. Abre una terminal en esta carpeta, donde se encuentran `docker-compose.yml` y `voice_actors_mongodb.json`.
2. Inicia los tres nodos del replica set:

   ```bash
   docker compose up -d
   ```

3. Comprueba que los contenedores estén ejecutándose:

   ```bash
   docker compose ps
   ```

## Conectar desde MongoDB Compass

1. Abre MongoDB Compass.
2. Utiliza la siguiente cadena de conexión:

   ```text
   mongodb://localhost:30001,localhost:30002,localhost:30003/?replicaSet=my-replica-set
   ```

3. Pulsa **Connect**.
4. Crea la base de datos `Actors` y la colección `Voice-actors`.
5. Abre la colección y selecciona **Add Data > Import JSON or CSV file**.
6. Selecciona el archivo `voice_actors_mongodb.json` incluido en esta carpeta y confirma la importación como JSON.

## Solucionar errores de conexión

Si Compass no puede conectarse o muestra un error relacionado con los nombres `mongo1`, `mongo2` o `mongo3`, añade estos nombres al archivo `hosts` de Windows:

1. Abre el Bloc de notas como administrador.
2. Selecciona **Archivo > Abrir**.
3. Ve a `C:\Windows\System32\drivers\etc`.
   - La letra de la unidad puede ser diferente en cada equipo.
   - Cambia el filtro de archivos a **Todos los archivos** para poder ver `hosts`.
4. Abre el archivo `hosts` y añade al final:

   ```text
   127.0.0.1 mongo1
   127.0.0.1 mongo2
   127.0.0.1 mongo3
   ```

5. Guarda el archivo y vuelve a intentar la conexión desde Compass.

## Ejecutar las consultas

Después de conectarte en Compass, pulsa **Open MongoDB shell** en la parte superior derecha. Desde esa consola puedes ejecutar los comandos incluidos en el informe sobre la base de datos `Actors` y la colección `Voice-actors`.

## Detener los contenedores

Para detener el replica set, ejecuta:

```bash
docker compose down
```

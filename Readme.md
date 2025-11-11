# Instalacion Odoo 18

--- 

### Utilicé PyCharm que ya venia instalada en el sistema
### Extensiones:
solo descargué la extensión de Docker, ya que era la que necesitaba para que el archivo .yml se ejecutara sin problemas
![Captura desde 2025-11-10 11-43-07.png](Captura%20desde%202025-11-10%2011-43-07.png)

---

## Docker-compose.yml 
Para el docker compose, busque la documentación dentro de Docker Hub para Odoo y para PgAdmin, ya que no se encuentra mucha información dentro de la misma pagina de docker hub, utilicé un ejemplo de "[Artículo de Geoinnova sobre PostgreSQL y pgAdmin con Docker](https://geoinnova.org/blog-territorio/postgresql-y-pgadmin-con-docker/ "Leer en Geoinnova")
". Especificamente en el apartado: **Gestionar la base de datos con pgAdmin**, editando algunas cosas como restart, puerto, enviroment, con configuración especificas de la bd 
```aiignore
services:
  web:
    image: odoo:18.0
    depends_on:
      - db
    ports:
      - "8069:8069"
    environment:
      HOST: db
      USER: odoo
      PASSWORD: odoo


  db:
    image: postgres:latest
    environment:
       POSTGRES_DB: postgres
       POSTGRES_PASSWORD: odoo
       POSTGRES_USER: odoo



  pgadmin:
    image: dpage/pgadmin4:latest
    environment:
      PGADMIN_DEFAULT_EMAIL: admin@pgadmin.com
      PGADMIN_DEFAULT_PASSWORD: password
      PGADMIN_LISTEN_PORT: 80
    ports:
      - "8081:80"
    depends_on:
      - db

```
Luego desde la consola del IDE lance el docker con el comando 
```bash
docker compose up
```
Probé los puertos:
```
http://localhost:8069
```
```
http://localhost:8081/
```
---
Si todo marcha bien, se mostrará el inicio de Odoo y PgAdmin (el login), donde nos logearemos
![Captura desde 2025-11-10 11-41-05.png](Captura%20desde%202025-11-10%2011-41-05.png)
![Captura desde 2025-11-10 11-41-54.png](Captura%20desde%202025-11-10%2011-41-54.png)
---
Luego de logearnos podremos ingresar a dichas interfaces

__Interfaz de Odoo__
![Captura desde 2025-11-10 11-40-18.png](Captura%20desde%202025-11-10%2011-40-18.png)
__Interfaz de PgAdmin__
![Captura desde 2025-11-10 11-41-33.png](Captura%20desde%202025-11-10%2011-41-33.png)

---

## Explorar Odoo
Descargué algunos modulos básicos que pedia la tarea como:

__(Para descargar dichos modulos solo hay que clicar en "Activar" y procedera a descargarse)__
 - Ventas: 
![Captura desde 2025-11-10 11-52-56.png](Captura%20desde%202025-11-10%2011-52-56.png)
 - Compras:
![Captura desde 2025-11-10 11-54-40.png](Captura%20desde%202025-11-10%2011-54-40.png)
 - Contactos: 
![Captura desde 2025-11-10 11-53-42.png](Captura%20desde%202025-11-10%2011-53-42.png)

## Base de datos PgAdmin
En PgAdmin introducimos/Creamos un servidor de forma manual
![Captura desde 2025-11-11 14-27-39.png](Captura%20desde%202025-11-11%2014-27-39.png)
![Captura desde 2025-11-11 14-27-39.png](Captura%20desde%202025-11-11%2014-27-39.png)
Luego de ingresar el servidor, para comprobar que si se creo, lo podemos ver en la barra lateral de la izquierda
![Captura desde 2025-11-11 14-00-58.png](Captura%20desde%202025-11-11%2014-00-58.png)
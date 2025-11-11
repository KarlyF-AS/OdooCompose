# Instalacion Odoo 18

--- 

## Utilicé PyCharm que ya venia insatlado en el sistema y las extensiones que utilicé son:
solo descargué la extensión de DOcker, porque era la que necesitaba para que el archivo .yml se ejecutara sin problemas
![Captura desde 2025-11-10 11-43-07.png](Captura%20desde%202025-11-10%2011-43-07.png)

---

## Docker-compose.yml 
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
Interfaz de Odoo
![Captura desde 2025-11-10 11-40-18.png](Captura%20desde%202025-11-10%2011-40-18.png)
Interfaz de PgAdmin
![Captura desde 2025-11-10 11-41-33.png](Captura%20desde%202025-11-10%2011-41-33.png)

---
## Explorar Odoo
Descargue algunos modulos básicos que pedia la tarea como
 - Ventas: 
![Captura desde 2025-11-10 11-52-56.png](Captura%20desde%202025-11-10%2011-52-56.png)
 - Compras:
![Captura desde 2025-11-10 11-54-40.png](Captura%20desde%202025-11-10%2011-54-40.png)
 - Contactos: 
![Captura desde 2025-11-10 11-53-42.png](Captura%20desde%202025-11-10%2011-53-42.png)

## Base de datos PgAdmin
![Captura desde 2025-11-11 13-57-15.png](Captura%20desde%202025-11-11%2013-57-15.png)

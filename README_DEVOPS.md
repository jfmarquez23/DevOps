###DevOps
#Habilidades
*Administracion de sistemas GNU/Linux
*Conocmiento de GIT
*Conocmiento de CI/CD (integracion y despliegue continuo)
*Conocmiento requerido (valido para plataformas Cloud y On-Premise)
*Administracion de Kuberbetes
*Administracion de Docker
*IaC con cualquier proveedor (idealmente utilizando terraform)
*Manejo basico de Python, Java, o Node (cualquiera de estos lenguajes de programacion)

*Habilidades deseables
Administracion Cloud Computing (Microsoft Azure, Amazon AWS, Google Cloud Plataform, otras).

#Ejercicio practico DevOps
*Para realizar el ejercicio propuesto se utilizo la siguiente aplicacion:
Python: https://bitbucket.org/devsu/demo-devops-python/src/master/

#Desarrollar los siguientes puntos:
**Dockerizar la aplicacion. Sientase libre de mejorar/cambiar y agregar lo que crea necesario.
*env vars.
*run user.
*port.
*healthcheck
*etc.

#Se encuentra creado el dockerfile con los puntos solicitidos en el repositorio GitHub:
https://github.com/jfmarquez23/DevOps.git


**Se debe generar un pipeline como codigo que idealmente incluya los siguientes pasos:
*Code Build
*Unit Test
*Static Code analysis
*Code coverage
*Contruir y subir la imagen (Docker build & push)
*Opcionales
  -Vulnerability Scan
  -Puede agregar nuevos test si lo cree necesario
#Se encuentra creado el pipeline con lo solicitado:Pipeline_Prueba_CI.yml en la ruta:
github/workflows/Pipeline_Prueba_CI.yml
  
  
**Desplegar la aplicacion dockerizada en Kubernetes, no se requiere que utilice un entorno publico, puede utilizar minikube/docker-desktop en un 
entorno local. Intente utilizar todos los recursos que cree necesario, es decir lo que utilizaria para q la app este productiva. 
Se requiere por lo menos 2 replicas y escalamiento horizantal.
*Configmaps
*Secrets
*Ingress
*etc.
#Se dockerizo con el archivo: prueba.yml ubicado en la ruta de github:
K8S/prueba.yml


*Agregar en el pipline el despliegue a Kubernetes.
K8S/imagen_docker.yml

*Documentacion en el archivo README.md que incluya :
-Diagranas
-Si hizo el despliegue en un entorno publicamente accesible por favor comparta la URL para poder validar el acceso.

**La revision se enfocara en:
*La correcta creacion de la imagen de docker.
*La correcta utilización de los recursos de Kubernetes.
*La correcta implementacion del pipeline.
*Prolojidad, documentacion, diagramas y todo lo que pueda ayudar al corrector a comprender las decisiones tomadas en cuenta.
*En caso de no haber cumplido con algun requerimiento, favor indicar el motivo.
*Adicionalmente si cree que hay algun contenido adicional que deba tenerse en cuenta para el correcto despliegue de la aplicacion en 
Produccion, no dude en agregarlo: DNS, certificado, tls, etc.
*La revision se enfocara en el seguimiento de buenas practicas y calidad del codigo.


Puntos extra: Se daran puntos adicionales si crea la infraestructura usando IaC en un proveedor publico, Se deberan subir los archivos 
correspondientes al despliegue y las salidas correspondientes al mismo en Terraform (apply/outpout), cloud formation (event/resources), etc. 

    




























# Demo Devops Python

This is a simple application to be used in the technical test of DevOps.

## Getting Started

### Prerequisites

- Python 3.11.3

### Installation

Clone this repo.

```bash
git clone https://bitbucket.org/devsu/demo-devops-python.git
```

Install dependencies.

```bash
pip install -r requirements.txt
```

Migrate database

```bash
py manage.py makemigrations
py manage.py migrate
```

### Database

The database is generated as a file in the main path when the project is first run, and its name is `db.sqlite3`.

Consider giving access permissions to the file for proper functioning.

## Usage

To run tests you can use this command.

```bash
py manage.py test
```

To run locally the project you can use this command.

```bash
py manage.py runserver
```

Open http://localhost:8000/api/ with your browser to see the result.

### Features

These services can perform,

#### Create User

To create a user, the endpoint **/api/users/** must be consumed with the following parameters:

```bash
  Method: POST
```

```json
{
    "dni": "dni",
    "name": "name"
}
```

If the response is successful, the service will return an HTTP Status 200 and a message with the following structure:

```json
{
    "id": 1,
    "dni": "dni",
    "name": "name"
}
```

If the response is unsuccessful, we will receive status 400 and the following message:

```json
{
    "detail": "error"
}
```

#### Get Users

To get all users, the endpoint **/api/users** must be consumed with the following parameters:

```bash
  Method: GET
```

If the response is successful, the service will return an HTTP Status 200 and a message with the following structure:

```json
[
    {
        "id": 1,
        "dni": "dni",
        "name": "name"
    }
]
```

#### Get User

To get an user, the endpoint **/api/users/<id>** must be consumed with the following parameters:

```bash
  Method: GET
```

If the response is successful, the service will return an HTTP Status 200 and a message with the following structure:

```json
{
    "id": 1,
    "dni": "dni",
    "name": "name"
}
```

If the user id does not exist, we will receive status 404 and the following message:

```json
{
    "detail": "Not found."
}
```

## License

Copyright © 2023 Devsu. All rights reserved.

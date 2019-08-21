# Notas swagger

Contenido obtenido de:  
* Creando un API REST con Swagger Node (https://medium.com/@diegopm2000/creando-un-api-rest-con-swagger-node-c880bdac04a5) 

## Qué es REST  

REST (Representational State Transfer) es un estilo de arquitectura de software, que podríamos definir cómo:

1. Todo es un recurso y viene representado por un formato.
2. Cada recurso tiene un único identificador y es accesible mediante una URI.  
3. Para operar con un recurso usaremos los típicos verbos (o métodos) de HTTP (GET, POST, PUT, DELETE, PATCH,…)  
4. Cada recurso puede tener múltiples representaciones (por ejemplo se podría representar mediante json, yaml, o xml).  
5. El protocolo de comunicación se considera sin estado (cada operación con el recurso se trata de forma totalmente aislada e independiente).    

## Instalación de Swagger Node

Vamos a usar el módulo de Swagger para NodeJS como herramienta principal para definir nuestro API Rest, y poder probarla sin tener en cuenta inicialmente ciertos detalles de implementación.  

Necesitamos instalar Swagger en nuestro sistema de forma global, usando el gestor de paquetería de NodeJS, para ello, desde un terminal de nuestro ordenador, escribiremos:  

    $ npm install -g swagger   
  Comprobamos que se ha instalado correctamente:  
  
      $ swagger — version  
      0.7.5  

## Creación del proyecto

Para crear la carpeta del proyecto y una serie de ficheros iniciales de Swagger, basta con situarnos en la carpeta que lo contendrá y escribir en el terminal:  

    $ swagger project create nombreproyecto
Se nos da para elegir el framework que queremos usar, escogeremos express. 

Nos creará la siguiente estructura de carpetas:  

* En la carpeta api, es dónde se implementará toda la lógica de la aplicación.
* En la carpeta config, podremos definir la configuración específica de la aplicación.
* Tenemos también la típica carpeta node_modules de todo proyecto de Node que use librerías externas.
* Los test unitarios, lógicamente los habremos de poner en la carpeta test.
* Además, en la raíz del proyecto tenemos el fichero habitual package.json y un fichero app.js típico de Express, que es el framework web que hemos decidido utilizar.  

Podemos levantar swagger en modo mock para que nos permita probar la api.
    $ swagger project start -m
## Ficheros importantes

## api/swagger/swagger.yml: Fichero de configuración

Campos fichero swagger.yml
* x-swagger-router-controller definimos el nombre del controlador que se encargará de procesar la petición /hello.
* Además hemos definido con operationId que en el controlador, la operación get será implementada en el método hello.
* Usamos la zona de parameters para definir los parámetros de entrada, que en este caso es sólo uno, ‘name’, viene por la querystring, no es obligatorio y es de tipo cadena.
* En la zona de responses, indicamos que si devolveremos el código http 200 devolveremos la referencia en la zona de definitions (situada más abajo) donde definimos la estructura de los datos devueltos.
* También tenemos una zona de default para otro caso, definiendo un ErrorResponse, también en la zona de definitions.

### api/controllers/hello_world.js Implementación del API

## Guía de códigos HTTP para API Rest: buenas prácticas  

<pre>
    <table class="table table-striped table-bordered">
						<thead>
							<tr>
								<th>HTTP Verb</th>
								<th>CRUD</th>
								<th>Entire Collection (e.g. /customers)</th>
								<th>Specific Item (e.g. /customers/{id})</th>
							</tr>
						</thead>
						<tbody>
							<tr>
								<td>POST</td>
								<td>Create</td>
								<td>201 (Created), 'Location' header with link to /customers/{id} containing new ID.</td>
								<td>404 (Not Found), 409 (Conflict) if resource already exists..</td>
							</tr>
							<tr>
								<td>GET</td>
								<td>Read</td>
								<td>200 (OK), list of customers. Use pagination, sorting and filtering to navigate big lists.</td>
								<td>200 (OK), single customer. 404 (Not Found), if ID not found or invalid.</td>
							</tr>
							<tr>
								<td>PUT</td>
								<td>Update/Replace</td>
								<td>405 (Method Not Allowed), unless you want to update/replace every resource in the entire collection.</td>
								<td>200 (OK) or 204 (No Content).  404 (Not Found), if ID not found or invalid.</td>
							</tr>
							<tr>
								<td>PATCH</td>
								<td>Update/Modify</td>
								<td>405 (Method Not Allowed), unless you want to modify the collection itself.</td>
								<td>200 (OK) or 204 (No Content).  404 (Not Found), if ID not found or invalid.</td>
							</tr>
							<tr>
								<td>DELETE</td>
								<td>Delete</td>
								<td>405 (Method Not Allowed), unless you want to delete the whole collection—not often desirable.</td>
								<td>200 (OK).  404 (Not Found), if ID not found or invalid.</td>
							</tr>
                        </tbody>
                    </table>
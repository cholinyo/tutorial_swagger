#Notas swagger

Contenido obtenido de [enlace}( https://medium.com/@diegopm2000/creando-un-api-rest-con-swagger-node-c880bdac04a5 )

## Qué es REST  
REST (Representational State Transfer) es un estilo de arquitectura de software, que podríamos definir cómo:
1.  Todo es un recurso y viene representado por un formato.  
2.  Cada recurso tiene un único identificador y es accesible mediante una URI.  
3.  Para operar con un recurso usaremos los típicos verbos (o métodos) de HTTP (GET, POST, PUT, DELETE, PATCH,…)  
4.  Cada recurso puede tener múltiples representaciones (por ejemplo se podría representar mediante json, yaml, o xml).  
5.  El protocolo de comunicación se considera sin estado (cada operación con el recurso se trata de forma totalmente aislada e independiente).    

## Instalación de Swagger Node
Vamos a usar el módulo de Swagger para NodeJS como herramienta principal para definir nuestro API Rest, y poder probarla sin tener en cuenta inicialmente ciertos detalles de implementación.  

Necesitamos instalar Swagger en nuestro sistema de forma global, usando el gestor de paquetería de NodeJS, para ello, desde un terminal de nuestro ordenador, escribiremos:  

    $ npm install -g swagger   
  Comprobamos que se ha instalado correctamente:  
      $ swagger — version  
      0.7.5  





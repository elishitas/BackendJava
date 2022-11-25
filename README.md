# Guía BackendJava

## Introducción

Esta es una guía para conocer más sobre JAVA y la creación de APIS con Spring Boot


## Semana 1
- Introducción (ya lo leíste)
- [Definición de API](#Definición-de-API)
- [Tipos de APIS](#Tipos-de-APIS)
- [Funcionamiento de las APIS](#Funcionamiento-de-las-APIS)
- [Definición de JSON](#Definición-de-JSON)
- [Definición de controller](#Definición-de-controller)
- [Creación de un RestController] (#Creación-de-un-RestController)

# Definición de API

Las **API** son mecanismos que permiten a dos componentes de software **comunicarse** entre sí mediante un conjunto de definiciones y protocolos. 

API significa “interfaz de programación de aplicaciones”. 

En el contexto de las API, la palabra aplicación se refiere a cualquier software con una función distinta. 

La interfaz puede considerarse como un contrato de servicio entre dos aplicaciones. Este contrato define cómo se comunican entre sí mediante solicitudes y respuestas. 

La documentación de una API contiene información sobre cómo developers deben estructurar esas solicitudes y respuestas.

# Tipos de APIS

- **API privadas**

Estas son internas de una empresa y solo se utilizan para conectar sistemas y datos dentro de la empresa.

- **API públicas**

Están abiertas al público y cualquier persona puede utilizarlas. Puede haber o no alguna autorización y coste asociado a este tipo de API.

- **API compuestas**

Estas combinan dos o más API diferentes para abordar requisitos o comportamientos complejos del sistema.

- **API de socios**

Solo pueden acceder a ellas los desarrolladores externos autorizados para ayudar a las asociaciones entre empresas.

# Funcionamiento de las APIS

La arquitectura de las API suele explicarse en términos de **cliente** y **servidor**. La aplicación que envía la solicitud se llama **cliente**, y la que envía la respuesta se llama **servidor**. 

Las API pueden funcionar de cuatro maneras diferentes, según el momento y el motivo de su creación.

- **API de SOAP**

Estas API utilizan el protocolo simple de acceso a objetos. El cliente y el servidor intercambian mensajes mediante XML. Se trata de una API menos flexible que era más popular en el pasado.

- **API de RPC**

Estas API se denominan llamadas a procedimientos remotos. El cliente completa una función (o procedimiento) en el servidor, y el servidor devuelve el resultado al cliente.

- **API de WebSocket**

La API de WebSocket es otro desarrollo moderno de la API web que utiliza objetos JSON para transmitir datos. La API de WebSocket admite la comunicación bidireccional entre las aplicaciones cliente y el servidor. El servidor puede enviar mensajes de devolución de llamada a los clientes conectados, por lo que es más eficiente que la API de REST.

- **API de REST**

Estas son las API más populares y flexibles que se encuentran en la web actualmente. El cliente envía las solicitudes al servidor como datos. El servidor utiliza esta entrada del cliente para iniciar funciones internas y devuelve los datos de salida al cliente.

# Definición de JSON

JavaScript Object Notation (JSON) es un formato basado en texto estándar para representar datos estructurados en la sintaxis de objetos de JavaScript. 

Es comúnmente utilizado para transmitir datos en aplicaciones web (por ejemplo: enviar algunos datos desde el servidor al cliente, así estos datos pueden ser mostrados en páginas web, o vice versa).

Ejemplo de un JSON:


``` json
{
  "squadName": "Super hero squad",
  "homeTown": "Metro City",
  "formed": 2016,
  "secretBase": "Super tower",
  "active": true,
  "members": [
    {
      "name": "Molecule Man",
      "age": 29,
      "secretIdentity": "Dan Jukes",
      "powers": [
        "Radiation resistance",
        "Turning tiny",
        "Radiation blast"
      ]
    },
}
```
# Definición de controller

Un *controller* es un componente de Spring capaz de recibir peticiones **http** y responderlas.

Las clases que definimos como un *controller* es responsable de procesar las llamadas entrantes (**request**) que ingresan a nuestra aplicación, validarlas y dar una respuesta (**response**).

Un *rest controller* es un tipo de *controller* que reciben peticiones con un formato de específico que cumple con formatos de solicitud RESTful habitualmente y mayormente en JSON , aunque a veces se usan otros como HTML, XML, o simplemente texto.

# Creación de un RestController

El primer paso para crear un ‘controlador rest’ es con la clase *@RestController*.

Con esto Spring ya sabe que esa clase será un componente encargado de recibir llamadas.

```
@RestController
public class HelloWordController {
}
```
Una vez que hemos anotado la clase podemos definir el método y la ruta en la cual recibirá la llamada externa.

Anotamos el método que da respuesta con *@GetMapping* y le indicamos la ruta en la cual responderá . Aquí definimos el path “/hello”.

```
@RestController
public class HelloWordController {

    @GetMapping("/hello")
    public String sayHello() {
        return "Hello dev";
    }

}
```
Arrancamos la aplicación.

Ahora podemos invocar nuestro *RestControler* mediante una llamada en el path ‘/hello’ que definimos previamente.

El servicio levanta en ‘localhost:8080’ y el path es ‘/hello’. Vemos la respuesta ‘Hello dev‘

![1](https://i.imgur.com/stlHrl7.png)





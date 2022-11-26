# Guía BackendJava

## Introducción

Esta es una guía para conocer más sobre JAVA y la creación de APIS con Spring Boot


## Semana 1
- Introducción (ya lo leíste)
- [Definición de API](#Definición-de-API)
- [Tipos de APIS](#Tipos-de-APIS)
- [Funcionamiento de las APIS](#Funcionamiento-de-las-APIS)
- [Funcionamiento de las APIS](#Funcionamiento-de-las-APIS)
- [REST](#REST)
- [HTTP-HTTPS](#HTTP-HTTPS)
- [Definición de JSON](#Definición-de-JSON)
- [Definición de controller](#Definición-de-controller)
- [Creación de un RestController] (#Creación-de-un-RestController)
- 

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

Una API de REST, o API de RESTful, es una interfaz de programación de aplicaciones (API o API web) que se ajusta a los límites de la arquitectura REST y permite la interacción con los servicios web de RESTful. El informático Roy Fielding es el creador de la transferencia de estado representacional (REST).

# REST

REST no es un protocolo ni un estándar, sino más bien un conjunto de límites de arquitectura. Las personas que desarrollan las API pueden implementarlo de distintas maneras.

Cuando el cliente envía una solicitud a través de una API de RESTful, esta transfiere una representación del estado del recurso requerido a quien lo haya solicitado o al extremo. La información se entrega por medio de HTTP en uno de estos formatos: JSON (JavaScript Object Notation), HTML, XLT, Python, PHP o texto sin formato. JSON es el lenguaje de programación más popular, ya que tanto las máquinas como las personas lo pueden comprender y no depende de ningún lenguaje, a pesar de que su nombre indique lo contrario -más adelante hay definición-. 

También es necesario tener en cuenta otros aspectos. Los encabezados y los parámetros también son importantes en los métodos HTTP de una solicitud HTTP de la API de RESTful, ya que contienen información de identificación importante con respecto a los metadatos, la autorización, el identificador uniforme de recursos (URI), el almacenamiento en caché, las cookies y otros elementos de la solicitud. Hay encabezados de solicitud y de respuesta, pero cada uno tiene sus propios códigos de estado e información de conexión HTTP.

Para que una API se considere de RESTful, debe cumplir los siguientes criterios:

- Arquitectura cliente-servidor compuesta de clientes, servidores y recursos, con la gestión de solicitudes a través de HTTP.
- Comunicación entre el cliente y el servidor sin estado, lo cual implica que no se almacena la información del cliente entre las solicitudes de GET y que cada una de ellas es independiente y está desconectada del resto.
- Datos que pueden almacenarse en caché y optimizan las interacciones entre el cliente y el servidor.
-Una interfaz uniforme entre los elementos, para que la información se transfiera de forma estandarizada. Para ello deben cumplirse las siguientes condiciones:
  - Los recursos solicitados deben ser identificables e independientes de las representaciones enviadas al cliente. 
  - El cliente debe poder manipular los recursos a través de la representación que recibe, ya que esta contiene suficiente información para permitirlo.
  - Los mensajes autodescriptivos que se envíen al cliente deben contener la información necesaria para describir cómo debe procesarla.
  - Debe contener hipertexto o hipermedios, lo cual significa que cuando el cliente acceda a algún recurso, debe poder utilizar hipervínculos para buscar   las demás acciones que se encuentren disponibles en ese momento.
- Un sistema en capas que organiza en jerarquías invisibles para el cliente cada uno de los servidores (los encargados de la seguridad, del equilibrio de carga, etc.) que participan en la recuperación de la información solicitada.
- Código disponible según se solicite (opcional), es decir, la capacidad para enviar códigos ejecutables del servidor al cliente cuando se requiera, lo cual amplía las funciones del cliente. 

Si bien la API de REST debe cumplir todos estos parámetros, resulta más fácil de usar que un protocolo definido previamente, como SOAP (protocolo simple de acceso a objetos), el cual tiene requisitos específicos, como la mensajería XML y la seguridad y el cumplimiento integrados de las operaciones, que lo hacen más lento y pesado. 

Por el contrario, REST es un conjunto de pautas que pueden implementarse según sea necesario. Por esta razón, las API de REST son más rápidas y ligeras, cuentan con mayor capacidad de ajuste y, por ende, resultan ideales para el Internet de las cosas (IoT) y el desarrollo de aplicaciones para dispositivos móviles. 

Resumen de Rest:
- Interfaz uniforme
- Separación entre c-s -cliente/servidor- -Diferente a MVC-
- Sin Estado 
- Capacidad de almacenamiento en caché
- Arquitectura de sistemas en capas -Cada capa tiene un rol específico-

![1](https://i.imgur.com/sPkYWBh.png)

# HTTP-HTTPS

HTTP es el acrónimo de Hypertext Transfer Protocol (en español protocolo de transferencia de hiper texto). HTTPS es igual pero añadiéndole "Seguro".
Estos dos protocolos se usan para lo mismo, la transferencia de datos. La diferencia básica entre ambos es la forma en la que viajan los datos.

La principal diferencia entre HTTP y HTTPS es la seguridad. El protocolo HTTPS impide que otros usuarios puedan interceptar la información confidencial
que se transfiere entre el cliente y el servidor web a través de Internet. Por decirlo de una manera muy sencilla, el protocolo HTTPS es la versión
segura del HTTP

![1](https://i.imgur.com/QSXvcq8.png)

# Definición de JSON

JavaScript Object Notation (JSON) es un formato basado en texto estándar para representar datos estructurados en la sintaxis de objetos de JavaScript. 

Es comúnmente utilizado para transmitir datos en aplicaciones web (por ejemplo: enviar algunos datos desde el servidor al cliente, así estos datos pueden
ser mostrados en páginas web, o vice versa).

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




